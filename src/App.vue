<template>
  <div>
    <table-component :data="data" :config="config">
    </table-component>
  </div>
</template>
<script>
import TableComponent from './components/TableComponent.vue'
import EventBus from './eventBus'
export default {
  components: {
    TableComponent
  }, 
  data: function () {
    return {
      data: [
      	{'name': 'Dan', 'age' : '26', 'job': 'Software Developer'}, 
      	{'name': 'Dale', 'age' : '36', 'job': 'Nascar Driver'}
      ],
      config:{
        editable: ['age', 'job'],
        actions: ['edit', 'delete'],
        types: {age : 'number'}
      }
    }
  }, 
  mounted () {
    EventBus.$on('SAVE_ROW', (changeData, dataIndex) => {
      console.log(changeData, dataIndex, 'SAVE_ROW')
      let ref = this;
      Object.keys(changeData).forEach(function (key) {
        ref.data[dataIndex][key] = changeData[key];
      });
    })
  }
}
</script>