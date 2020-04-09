<template>
  <b-table :data="data" :columns="columns"></b-table>
</template>

<script>
export default {
  props: {
    d: {
      type: Array,
      required: true
    },
    c: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      data: this.d,
      columns: this.c
    }
  }
}
</script>
