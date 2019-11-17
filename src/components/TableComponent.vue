<template>
  <table class="table">
	<thead>
	  <TableThComponent :ths="ths"></TableThComponent>
	</thead>
	<tbody>
	  <TableTrComponent v-for="(trData, key) in data"
  			:trData="trData"
  			:config="config"
  			v-bind:parKey="key"
  			v-bind:key="key"
  			v-on:deleteTr="deleteTr(key)"
		></TableTrComponent>
	</tbody>
  </table>
</template>
<script>
import Vue from 'vue'
import TableThComponent from './TableThComponent.vue'
import TableTrComponent from './TableTrComponent.vue'
export default {
  components: {
    TableThComponent, 
    TableTrComponent
  }, 
  props: {
    data: {
      type: Array,
      required: true
    }, 
    config:{
    	type: Object, 
    	required: true
    }
  }, 
  computed: {
    // a computed getter
    ths: function () {
      // `this` points to the vm instance
      return Object.keys(this.data[0]);
    }
  }, 
  methods: {
    deleteTr(index) {
      Vue.delete(this.data, index);
    }
  }
}
</script>
<style lang="stylus" scoped>
h1
  color red
</style>