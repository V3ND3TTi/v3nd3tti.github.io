<template>
  <canvas ref="canvas" class="hero-canvas"></canvas>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'
import * as THREE from 'three'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'
import gsap from 'gsap'

const canvas = ref(null)
const emit = defineEmits(["ready"])
const letters = []
let renderer, camera, scene, controls, animationId
let model = null
let iDot = null
let frame = null

onMounted(() => {
  // Scene
  scene = new THREE.Scene()
  scene.background = null

  // Camera
  camera = new THREE.PerspectiveCamera(
    45,
    window.innerWidth / window.innerHeight,
    0.1,
    100
  )
  updateCameraPosition()

  // Renderer
  renderer = new THREE.WebGLRenderer({
    canvas: canvas.value,
    antialias: true,
    alpha: true, // allow transparency
  })
  renderer.setSize(window.innerWidth, window.innerHeight)
  renderer.setPixelRatio(window.devicePixelRatio)
  renderer.setClearColor(0x000000, 0) // fully transparent

  // Controls (remove later if you want it fixed)
  controls = new OrbitControls(camera, renderer.domElement)

  // Lights
  const hemiLight = new THREE.HemisphereLight(0xffffff, 0x444444, 1.2)
  hemiLight.position.set(0, 20, 0)
  scene.add(hemiLight)

  const dirLight = new THREE.DirectionalLight(0xffffff, 1)
  dirLight.position.set(5, 10, 7.5)
  scene.add(dirLight)

  // Load GLB
  const loader = new GLTFLoader()
  loader.load('/models/vlogo.glb', (gltf) => {
    model = gltf.scene

    scene.add(model)

    model.traverse((child) => {
      if (child.isMesh) {
        if (child.name.toLowerCase().includes("idot")) {
          iDot = child
        } else if (child.name.toLowerCase().includes("frame")) {
          frame = child
        } else {
          letters.push(child)
        }
      }
    })
    runAnimation()
  })

  // Animate
  const animate = () => {
    animationId = requestAnimationFrame(animate)
    controls.update()
    renderer.render(scene, camera)
  }
  animate()

  // Listeners
  window.addEventListener('resize', onWindowResize)
  window.addEventListener('resize', updateCameraPosition)
})

onBeforeUnmount(() => {
  cancelAnimationFrame(animationId)
  window.removeEventListener('resize', onWindowResize)
  renderer.dispose()
})

function updateCameraPosition() {
  if (window.innerWidth < 768) {
    camera.position.set(0, 0, 12) // mobile
  } else {
    camera.position.set(0, 0, 5) // desktop
  }
  camera.lookAt(0, 0, 0)
}

function onWindowResize() {
  if (!model) return 

  const width = window.innerWidth
  const height = window.innerHeight

  camera.aspect = width / height
  camera.updateProjectionMatrix()
  renderer.setSize(width, height)

  if (model) {
    const box = new THREE.Box3().setFromObject(model)
    const size = new THREE.Vector3()
    box.getSize(size)

    // Get the max dimension (width or height of model)
    const maxDim = Math.max(size.x, size.y, size.z)

    let scale

    if (width < 768) {
      // Mobile: prioritize fitting to width
      scale = (width / maxDim) * 0.4
    } else {
      // Desktop: fit to smaller of width/height
      scale = (Math.min(width, height) / maxDim) * 0.4
    }

    model.scale.setScalar(scale)

    const center = box.getCenter(new THREE.Vector3())
    model.position.sub(center)
  }
}

function runAnimation() {
  // -------------------
  // Letters fly-in
  // -------------------
  letters.forEach((l, i) => {
    l.userData.targetPos = l.position.clone()
    l.userData.targetRot = { x: 0, y: 0, z: 0 }

    // Random scattered start
    l.position.set(
      (Math.random() - 0.5) * 10,
      (Math.random() - 0.5) * 6,
      (Math.random() - 0.5) * 10
    )
    l.rotation.set(
      Math.random() * Math.PI * 4,
      Math.random() * Math.PI * 4,
      Math.random() * Math.PI * 4
    )

    // Random duration/delay for organic motion
    const travelTime = 0.3 + Math.random() * 1.0   // 0.–1.5s
    const delay = Math.random() * 0.2             // offset up to 0.3s

    // Animate position
    gsap.to(l.position, {
      x: l.userData.targetPos.x,
      y: l.userData.targetPos.y,
      z: l.userData.targetPos.z,
      duration: travelTime,
      delay,
      ease: "power3.out"
    })

    // Animate rotation spin-down
    gsap.to(l.rotation, {
      x: l.userData.targetRot.x,
      y: l.userData.targetRot.y,
      z: l.userData.targetRot.z,
      duration: travelTime,
      delay,
      ease: "power3.out"
    })
  })

  // ------------------
  // iDot bounce-in
  // ------------------
  if (iDot) {
    iDot.userData.targetPos = iDot.position.clone()
    iDot.userData.targetRot = { x: 0, y: 0, z: 0 }

    // Start off-screen to the right, small variance in Y/Z
    iDot.position.set(
      8, 
      iDot.userData.targetPos.y + (Math.random() * 2 - 1),
      iDot.userData.targetPos.z + (Math.random() * 2 - 1)
    )
    iDot.rotation.set(
      Math.random() * 2,
      Math.random() * 2,
      Math.random() * 2
    )

    gsap.to(iDot.position, {
      x: iDot.userData.targetPos.x,
      y: iDot.userData.targetPos.y,
      z: iDot.userData.targetPos.z,
      duration: 1,
      delay: 0.5, // comes after letters, but not too late
      ease: "back.out(2)"
    })

    gsap.to(iDot.rotation, {
      x: 0, y: 0, z: 0,
      duration: 1,
      delay: 0.5,
      ease: "power2.out"
    })
  }


  // ------------------
  // Frame fly-through
  // ------------------
  if (frame) {
    frame.userData.targetPos = frame.position.clone()
    frame.userData.targetRot = { x: 0, y: 0, z: 0 }

    // Start just above / in front of the camera
    frame.position.set(0, 5, 10) // y = 5 for "overhead", z = 10 is in front of camera
    frame.rotation.set(0, 0, 0)  // no spin

    gsap.to(frame.position, {
      x: frame.userData.targetPos.x,
      y: frame.userData.targetPos.y,
      z: frame.userData.targetPos.z,
      duration: 1,
      delay: 1.5, // comes after iDot
      ease: "power2.out",
      onComplete: () => {
        emit("ready")
      }
    })
  }
}

function skipToEnd() {
  // Instantly set everything to final state
  letters.forEach(l => {
    if (l.userData?.targetPos) {
      l.position.copy(iDot.userData.targetPos)
      l.rotation.set(0, 0, 0)
    }
  })

  if (iDot && iDot.userData?.targetPos) {
    iDot.position.copy(iDot.userData.targetPos)
    iDot.rotation.set(0, 0, 0)
  }

  if (frame && frame.userData?.targetPos) {
    frame.position.copy(frame.userData.targetPos)
    frame.rotation.set(0, 0, 0)
  }
  emit("ready")
}
</script>

<style scoped>
.hero-canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 5;
  display: block;
}
</style>
