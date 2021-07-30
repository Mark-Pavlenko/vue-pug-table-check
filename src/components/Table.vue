<template lang="pug">
  div(id="app")
    vue-good-table( :columns="columns" :rows="rows")
      template(slot='table-row' slot-scope='props')
        span(class='wrap' v-if="props.column.field == 'age'")
          span(:class="getCellClass(props.row.age)") {{ props.row.age }}
        span(v-else) {{ props.formattedRow[props.column.field] }}
</template>

<script>
export default {
  data() {
    return {
      columns: [
        {
          label: 'Name',
          field: 'name',
        },
        {
          label: 'Age',
          field: 'age',
          type: 'number',
        },
        {
          label: 'Percent',
          field: 'score',
          type: 'percentage',
        },
      ],
      rows: [
        {id: 1, name: "John", age: Math.floor(Math.random() * 10), createdAt: '201-10-31:9: 35 am', score: 0.03343},
        {id: 2, name: "Jane", age: Math.floor(Math.random() * 10), createdAt: '2011-10-31', score: 0.03343},
        {id: 3, name: "Susan", age: Math.floor(Math.random() * 10), createdAt: '2011-10-30', score: 0.03343},
        {id: 4, name: "Chris", age: Math.floor(Math.random() * 10), createdAt: '2011-10-11', score: 0.03343},
        {id: 5, name: "Dan", age: Math.floor(Math.random() * 10), createdAt: '2011-10-21', score: 0.03343},
      ],
    };
  },
  methods: {
    getCellClass(age) {
      return age > 5 ? 'is-green' : '';
    },
  },
}
</script>

<style scoped>

#app {
  padding: 20px;
}

.wrap {
  display: block;
  position: relative;
  width: 100%;
}

.is-green {
  background: green;
  color: white;
  position: absolute;
  left: -0.75rem;
  right: -0.75rem;
  top: -0.75rem;
  bottom: -1.9rem;
  padding: 0.75rem;
}

</style>

