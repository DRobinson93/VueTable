<template>
   <td>
    <span v-if="editMode && editable">
      <input :type="inputType" v-model="internalVal" v-on:change="$emit('editTd', index, internalVal)"></input>
    </span>
    <span v-else>
    {{ val }}
    </span>
   </td>
</template>
<script>
export default {
  methods: {
    handleChange(){
      this.$emit('editTd(this.internalVal)')
    }
  },
  computed: {
    // a computed getter
    inputType: function () {
      return this.config.types.hasOwnProperty(this.index) ? 
        this.config.types : 'text'
    }, 
    editable: function () {
      return this.config.editable.includes(this.index)
    }
  },
  data(){
    return {
      internalVal: this.val
    }
  },
  props: ['editMode', 'val', 'index', 'config']
}
</script>