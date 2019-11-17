<template>
  <td>
    <span v-if="showEditBtn">
      <button class="btn btn-secondary" v-on:click="$emit('editTr')">Edit</button>
    </span>
    <span v-else>
      <button class="btn btn-secondary" v-on:click="$emit('saveTr')">Save</button>
    </span>
    <span v-if="actions.includes('delete')">
      <button class="btn btn-secondary" v-on:click="$emit('deleteTr')">Delete</button>
    </span>
  </td>
</template>
<script>
export default {
   props: {
    editMode: {
      type: Boolean,
      required: true
    },
    actions: {
      type: Array,
      required: true
    }
  },
  computed: {
    showEditBtn: function () {
      return this.actions.includes('edit') && !this.editMode;
    }
  } 
}
</script>