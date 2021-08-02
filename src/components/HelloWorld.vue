<template lang="pug">
  div
    table(style='width:100%', border='1')
      tr
        th Id
        th Name
        th Number
      tr(v-for='item in items' :key="item.id")
        td {{item.id}}
        td {{item.name}}
        td(  :class="{ bgDanger: checkValidValue(item) }") {{item.number}}
      tr

    button(@click="checkValidValue") Check

</template>

<script>

export default {
  data: function () {
    return {
      items: [
        {
          id: 1,
          name: 'Adam',
          number: Math.floor(Math.random() * 20)
        },
        {
          id: 2,
          name: 'Smith',
          number: Math.floor(Math.random() * 20)
        },
        {
          id: 3,
          name: 'Jane',
          number: Math.floor(Math.random() * 20)
        },
        {
          id: 4,
          name: 'Tom',
          number: Math.floor(Math.random() * 20)
        },
        {
          id: 5,
          name: 'Sam',
          number: Math.floor(Math.random() * 20)
        }
      ]
    };
  },
  methods: {
    checkValidValue(items){
      return items.number > 5;
    }
  },
  mounted() {
    // this.getExtraElements();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
  font-family: arial, sans-serif;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}

.bgDanger{
  border: 1px solid red;
}

</style>
