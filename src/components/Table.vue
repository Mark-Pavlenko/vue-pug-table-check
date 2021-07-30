<template>
  <div id="app">
    <vue-good-table
        :columns="columns"
        :rows="rows">
      <template slot="table-row" slot-scope="props">
      <span
          class="wrap"
          v-if="props.column.field == 'age.max'">
        <span :class="getCellClass(props.row.age.max)">
          {{ props.row.age.max }}
        </span>
      </span>
        <span v-else>
        {{ props.formattedRow[props.column.field] }}
      </span>
      </template>
    </vue-good-table>
  </div>
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
          field: 'age.max',
          type: 'number',
        },
        {
          label: 'Percent',
          field: 'score',
          type: 'percentage',
        },
      ],
      rows: [
        {id: 1, name: "John", age: {min: 20, max: 24}, createdAt: '201-10-31:9: 35 am', score: 0.03343},
        {id: 2, name: "Jane", age: {min: 16, max: 21}, createdAt: '2011-10-31', score: 0.03343},
        { id:3, name:"Susan", age: { min: 45, max: 55 }, createdAt: '2011-10-30', score: 0.03343 },
        {id: 4, name: "Chris", age: {min: 16, max: 21}, createdAt: '2011-10-11', score: 0.03343},
        {id: 5, name: "Dan", age: {min: 16, max: 21}, createdAt: '2011-10-21', score: 0.03343},
      ],
    };
  },
  methods: {
    getCellClass(age) {
      return age > 21 ? 'is-green' : '';
    },
  },
}
</script>

<style scoped>

#app{
  padding: 20px;
}

.wrap{
  display: block;
  position: relative;
  width: 100%;
}

.is-green{
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

