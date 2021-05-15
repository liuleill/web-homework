<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>
<script>
import Chart from './chart.vue';
export default {
  data () {
    return {
      cdata: {
        xData: ["大豆", "幼苗", "蜜桔", "花生"],
        seriesData: [
          { value: 10, name: "大豆" },
          { value: 5, name: "幼苗" },
          { value: 15, name: "蜜桔" },
          { value: 25, name: "花生" },
        ]
      }
    }
  },
  components: {
    Chart,
  },
  mounted () {
  },
  methods: {
  }
}
</script>
<style lang="scss" scoped>
</style>