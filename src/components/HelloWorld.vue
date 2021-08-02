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
        td( v-bind:class="{ bgDanger: customerStatusIsTwo(item) }") {{item.number}}
      tr

    //button(@click="showMobileMenu = !showMobileMenu") Check
    button(@click="customerStatusIsTwo") Check

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
      ],
      // allItemsNumbers: [],
      // extraNumbers: [],
      // showMobileMenu: false
    };
  },
  methods: {
    // getExtraElements() {
    //   for(let i =0; i < this.items.length; i++){
    //     this.allItemsNumbers.push(this.items[i].number);
    //   }
    //   console.log(this.allItemsNumbers);
    //   this.extraNumbers = this.allItemsNumbers.filter(item => item > 5);
    //   console.log(this.extraNumbers);
    //
    //   //поэлементно сравнить 2 массива и там, где элементы второго массива сходятся с ключами - добавить класс???
    //
    //   this.showMobileMenu = !this.showMobileMenu
    // },
    customerStatusIsTwo : function(items){
      return items.number > 5
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

.default {
  color: red
}


.bgDanger{
  border: 1px solid red;
}

</style>
