<template>
  <div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h2>计划时间</h2>
      </div>
      <div class="panel-body">
        <h3>{{time | number}}小时</h3>
      </div>
    </div>
  </div>
</template>
<style scoped>

</style>

<script>
  import {mapState} from 'vuex';

  export default {
    filters:{
      number(input){
        return input.toFixed(2);
      }
    },
    data() {
      return {}
    },
    computed: {
      ...mapState({time: "totalTime"})
    },
    components: {},
    methods: {}
  }
</script>
