<template>
  <b-row v-loading="true" id="loading_formulario" name="loading_formulario" style="display: none;"></b-row>
</template>
<script>
import Vue from 'vue';
import { Loading } from 'element-ui';

Vue.use(Loading.directive);
export default {
  name:'loading-formulario',
  methods:{
    IsVisibly(visible){
      var loading = document.getElementsByTagName("loading_formulario")[0];
      if(visible){
        loading.style="display: block;";
      }else{
        loading.style="display: none;";
      }
    }
  }
};
</script>
<style>
#loading {
  min-height: 200px;
  display: flex;
  align-items: center;
}

.el-loading-spinner .path {
  stroke: #66615b !important;
}

.el-loading-mask {
  background: transparent !important;
}
</style>
