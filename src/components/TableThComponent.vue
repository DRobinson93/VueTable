<template>
  <tr>
   <th v-for="th in thsFormatted">
    {{ th }}
   </th>
  </tr>
</template>
<script>
export default {
  props: {
    ths: {
      type: Array,
      required: true
    }
  }, 
  computed: {
    // a computed getter
    thsFormatted: function () {
      let formatted = [];	
      this.ths.forEach(function(th){
		  formatted.push(th.toUpperCase())
		});
      // `this` points to the vm instance
      return formatted;
    }
  }
}
</script>