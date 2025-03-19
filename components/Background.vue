<template>
  <canvas
    ref='canvas'
    :width="width"
    :height="height"
  />
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'

const canvas = ref(null)
const ctx = ref(null)
const width = ref(null)
const height = ref(null)

let angle = 0
let speed = 0

const draw = (line) => {
  const slope = Math.tan(line.angle)

  const [intersectTop, intersectDown, intersectLeft, intersectRight] = [
    line.y + slope * (-line.x),
    line.y + slope * (width.value - line.x),
    line.x - line.y / slope,
    line.x + (height.value - line.y) / slope,
  ]

  ctx.value.beginPath()
  ctx.value.strokeStyle = 'rgba(100, 100, 100, 0.6)'

  if (intersectTop < 0) {
    ctx.value.moveTo(intersectLeft, 0)
  } else {
    ctx.value.moveTo(0, intersectTop)
  }

  if (intersectDown > width.value) {
    ctx.value.lineTo(intersectRight, height.value)
  } else {
    ctx.value.lineTo(width.value, intersectDown)
  }

  ctx.value.stroke()
}

const update = () => {
  const offset = Math.sin(performance.now() / 1000)

  angle = offset * Math.PI / 180
  speed = offset / 10 + 80

  ctx.value?.clearRect(0, 0, width.value, height.value)

  const deltaX = width.value / speed
  const deltaY = height.value / speed

  for (let displacement = -deltaX; displacement < deltaX * 2; displacement++) {
    draw({
      x: displacement * speed * Math.cos(angle + Math.PI / 2) + width.value / 2,
      y: displacement * speed * Math.sin(angle + Math.PI / 2) + height.value / 2,
      angle: angle + Math.PI,
    })
  }

  for (let displacement = -deltaY; displacement < deltaY; displacement++) {
    draw({
      x: displacement * speed * Math.cos(angle) + width.value / 2,
      y: displacement * speed * Math.sin(angle) + height.value / 2,
      angle: angle + Math.PI / 2,
    })
  }

  requestAnimationFrame(update)
}

const resizeCanvas = () => {
  width.value = window.innerWidth
  height.value = window.innerHeight
}

onMounted(() => {
  ctx.value = canvas.value.getContext('2d')

  resizeCanvas()

  window.addEventListener('resize', resizeCanvas)

  requestAnimationFrame(update)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', resizeCanvas)
})
</script>
