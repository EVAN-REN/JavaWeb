<template>
  <div>
    <!-- <h1>{{message}}</h1> -->
    <!-- <element-view></element-view> -->
    <!-- <emp-view-vue></emp-view-vue> -->
    <router-view></router-view>
  </div>
</template>

<script>
// import EmpViewVue from './views/tlias/EmpView.vue'
// import ElementView from './views/element/ElementView.vue'
export default {
  components: {/*EmpViewVue*//* ElementView*/},
  data(){
    return {
      message: "Hello Vue"
    }
  },
  methods: {
    
  },
}
</script>

<style>

</style>
