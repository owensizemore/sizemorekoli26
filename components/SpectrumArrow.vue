<script setup lang="ts">
import { nextTick, onBeforeUnmount, onMounted, ref } from 'vue'
import rough from 'roughjs'

const root = ref<HTMLElement | null>(null)
const svgEl = ref<SVGSVGElement | null>(null)

const HEIGHT = 44
const ARROW_Y = 18
const TICKS = [
  { at: 0.17, seed: 11 },
  { at: 0.83, seed: 19 },
  { at: 0.5, seed: 23 },
]

function strokeColor(el: Element) {
  return getComputedStyle(el).color || '#1f2937'
}

function lineOpts(color: string, seed: number) {
  return {
    stroke: color,
    strokeWidth: 2.4,
    roughness: 1.35,
    bowing: 0.8,
    seed,
  }
}

function drawArrow() {
  const svg = svgEl.value
  const wrap = root.value
  if (!svg || !wrap) return

  const width = wrap.clientWidth
  if (width < 40) return

  svg.setAttribute('viewBox', `0 0 ${width} ${HEIGHT}`)
  svg.replaceChildren()

  const color = strokeColor(wrap)
  const rc = rough.svg(svg)
  const y = ARROW_Y
  const pad = 10
  const headLen = 28
  const headSpread = 16
  const left = pad
  const right = width - pad
  const opts = lineOpts(color, 7)

  svg.appendChild(rc.line(left + headLen * 0.45, y, right - headLen * 0.45, y, opts))
  svg.appendChild(
    rc.polygon(
      [
        [left, y],
        [left + headLen, y - headSpread],
        [left + headLen, y + headSpread],
      ],
      { ...opts, fill: color, fillStyle: 'solid', roughness: 1.15 },
    ),
  )
  svg.appendChild(
    rc.polygon(
      [
        [right, y],
        [right - headLen, y - headSpread],
        [right - headLen, y + headSpread],
      ],
      { ...opts, fill: color, fillStyle: 'solid', roughness: 1.15 },
    ),
  )
}

function drawTicks() {
  const wrap = root.value
  if (!wrap) return
  const color = strokeColor(wrap)
  const svgs = wrap.querySelectorAll<SVGSVGElement>('.marker-tick')
  svgs.forEach((svg, i) => {
    const height = svg.clientHeight || 40
    const width = svg.clientWidth || 18
    svg.setAttribute('viewBox', `0 0 ${width} ${height}`)
    svg.replaceChildren()
    const rc = rough.svg(svg)
    svg.appendChild(
      rc.line(width / 2, 1, width / 2, height - 1, {
        ...lineOpts(color, TICKS[i].seed),
        strokeWidth: 2,
        bowing: 0.4,
      }),
    )
  })
}

function draw() {
  drawArrow()
  drawTicks()
}

let observer: ResizeObserver | null = null

onMounted(async () => {
  await nextTick()
  draw()
  observer = new ResizeObserver(() => draw())
  if (root.value) observer.observe(root.value)
})

onBeforeUnmount(() => {
  observer?.disconnect()
})
</script>

<template>
  <div ref="root" class="spectrum">
    <div class="spectrum-plot">
      <div class="spectrum-markers">
        <div class="marker marker-left" v-click="2">
          <div class="marker-label">Ban it, AI-proof everything</div>
          <svg class="marker-tick" />
        </div>
        <div class="marker marker-right" v-click="3">
          <div class="marker-label">Unrestricted AI use</div>
          <svg class="marker-tick" />
        </div>
        <div class="marker marker-center" v-click="4">
          <div class="marker-label">
            <span v-mark.underline.blue="5">Guide students toward responsible AI use</span>
          </div>
          <svg class="marker-tick" />
        </div>
      </div>
      <div class="spectrum-axis" v-click="1">
        <svg ref="svgEl" class="spectrum-svg" />
        <div class="spectrum-labels">
          <span>No AI use</span>
          <span>Lots of AI use</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.spectrum {
  width: calc(100% + 7rem);
  margin-left: -3.5rem;
  margin-right: -3.5rem;
  margin-top: 0.6rem;
  padding: 1.75rem 2.5rem 0;
}
.spectrum-plot {
  position: relative;
}
.spectrum-markers {
  position: absolute;
  inset: 0 0 auto 0;
  height: 3rem;
  z-index: 1;
  pointer-events: none;
}
.marker {
  position: absolute;
  bottom: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  transform: translateX(-50%);
  padding-bottom: 1.75rem;
}
.marker-left {
  left: 17%;
  width: 11.5rem;
}
.marker-right {
  left: 83%;
  width: 10.5rem;
}
.marker-center {
  left: 50%;
  width: 14.5rem;
}
.marker-label {
  flex: 0 0 auto;
  text-align: center;
  font-size: 1.05rem;
  font-weight: 500;
  line-height: 1.25;
}
.marker-tick {
  display: block;
  width: 18px;
  flex: 0 0 1.85rem;
  height: 1.85rem;
  overflow: visible;
}
.spectrum-svg {
  display: block;
  width: 100%;
  height: 44px;
  margin-top: 6.4rem;
  overflow: visible;
}
.spectrum-labels {
  display: flex;
  justify-content: space-between;
  padding: 0.1rem 0.85rem 0;
  font-size: 1.15rem;
  font-weight: 500;
  line-height: 1.3;
}
.spectrum :deep(.spectrum-axis.slidev-vclick-target) {
  transition: opacity 0.5s ease !important;
}
</style>
