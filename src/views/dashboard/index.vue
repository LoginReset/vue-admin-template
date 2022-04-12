<template>
  <div class="dashboard-container">
    <div class="dashboard-text">name: {{ name }}</div>
    <div>
      <el-image style="width: 1000px" :src="src"></el-image>
      <canvas id="canvas" class="ctx"></canvas>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import { fabric } from 'fabric'

const length = 30
export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  data() {
    return {
      src: 'https://cube.elemecdn.com/6/94/4d3ea53c084bad6931a56d5158a48jpeg.jpeg'
    }
  },
  mounted() {
    const canvas = new fabric.Canvas('canvas', {
      width: 500, height: 500
    })
    const rect = new fabric.Rect({
      top: 50,
      left: 100,
      width: 100,
      height: 100,
      fill: 'red'
    })
    canvas.add(rect)

    const points = [
      { x: length / 2, y: 0 },
      { x: length * 1.5, y: 0 },
      { x: length * 2, y: length * 3 ** 0.5 / 2 },
      { x: length * 1.5, y: length * 3 ** 0.5 },
      { x: length / 2, y: length * 3 ** 0.5 },
      { x: 0, y: length * 3 ** 0.5 / 2 }
    ]

    const six = new fabric.Polygon(points,
      {
        left: 0, top: 0, angle: 0,
        fill: 'green',
        border: 1
      })
    canvas.add(six)

    const six2 = new fabric.Polygon(points,
      {
        left: 100,
        top: 100,
        angle: 0,
        fill: 'green',
        border: 1
      }
    )
    canvas.add(six2)
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }

  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}

.ctx {
  width: 5000px;
  height: 5000px;
  border: 1px solid black;
}
</style>
