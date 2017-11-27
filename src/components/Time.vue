<template>
  <div>
    <router-link to="/time/time-add" class="btn btn-primary">创建</router-link>
    <hr>
    <router-view></router-view>

    <ul class="list-group" v-for="data in list">
      <li class="list-group-item">
        <div class="row">
          <div class="col-md-2 text-center">
            <img :src="data.avator" class="img-circle img-responsive">
            {{data.name}}
          </div>
          <div class="col-md-3">
            <div><i class="glyphicon glyphicon-time"></i>{{data.time}}小时

            </div>
            <div class="text-info">
              <i class="glyphicon glyphicon-calendar"></i>{{data.date}}
            </div>
          </div>
          <div class="col-md-5">
            {{data.comment}}
          </div>
          <div class="col-md-2">
            <button type="button" class="btn btn-danger" @click="remove(data)">&times;</button>
          </div>
        </div>
      </li>
    </ul>
    <div class="text-warning h2" v-show="!isShow">
      你的计划空空如也
    </div>
  </div>
</template>
<style scoped>
  div {
    line-height: 35px;
  }
</style>

<script>
  import {mapState, mapActions,mapGetters} from 'vuex';
  import * as Types from '@/store/types';

  export default {
    data() {
      return {}
    },
    computed: {
      ...mapGetters(['isShow']),
      ...mapState({list: 'lists'})
    },
    components: {},
    methods: {
      ...mapActions([Types.REMOVE_PLAN, Types.REMOVE_TOTALTIME]),
      remove(obj) {
        this[Types.REMOVE_PLAN](obj);
        this[Types.REMOVE_TOTALTIME](obj.time);
      }
    }
  }
</script>
