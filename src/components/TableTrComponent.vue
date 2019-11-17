<template>
  <tr>
    <TableTdComponent v-for="(val, index) in trData"
        :val="val"
        v-bind:index="index"
        v-bind:key="index"
        :config="config"
        :editMode="editMode"
        v-on:editTd="tdEdit"
    ></TableTdComponent>
    <TableActionTdComponent :editMode="editMode" 
          :actions="config.actions" v-on:deleteTr="$emit('deleteTr')"
          v-on:editTr="editBtnClick" v-on:saveTr="saveBtnClick"
          ></TableActionTdComponent>
  </tr>
</template>
<script>
import TableTdComponent from './TableTdComponent.vue'
import TableActionTdComponent from './TableActionTdComponent.vue'
import EventBus from '../eventBus'
export default {
  methods: {
    tdEdit(index, val){
      this.updateData[index] = val;
    },
    editBtnClick(){
       this.editMode = true;
    }, 
    saveBtnClick(){
      EventBus.$emit('SAVE_ROW', this.updateData, this.parKey)
      this.editMode = false;
    }
  },
  data: function () {
    return {
      editMode: false, 
      updateData:[]
    }
  },
  components: {
    TableTdComponent, 
    TableActionTdComponent
  }, 
  props: {
    parKey:{
      type: Number,
      required: true
    },
    trData: {
      type: Object,
      required: true
    }, 
    config:{
      type:Object, 
      required:true
    }
  }
}
</script>