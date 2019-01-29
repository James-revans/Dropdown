<template>
  <b-container fluid class="dropList p-0">
    <Item v-for="(item, index) in dropArr" :key='index'
      :value="item.value" v-on:updateValue="dropDownValue($event, item)"
      :fonticon="item.font_awesome_icon"/>
  </b-container>
</template>

<script>
import axios from "axios"
import Item from "@/components/Dropdown-item";



export default {
  components: {
    Item
  
    },
  
  data() {
    return {
      dropArr: []
    }
  },

  props: {
    msg: String
  },

  created() {
    var self = this;
    axios.get('https://api.myjson.com/bins/o2ebg')
    .then(function (response) {
        self.dropArr = response.data;
        console.log(response);
      })
    .catch(function (error) {
        console.log(error);
    });

  },
  methods: {
    dropDownValue: function(event, item) {
      item.value = event;
      console.log(this.dropArr);
    }
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .dropList {
    background: rgb(255, 255, 255);
    border-left: solid 5px rgb(61, 80, 117);
    border-bottom: solid 1px rgb(61, 80, 117);
    border-bottom-left-radius: 5px;
    margin: 0;
    max-height: 400px;
    overflow-y: scroll;
      ul{
      list-style-type: none;
    }
  }

</style>
