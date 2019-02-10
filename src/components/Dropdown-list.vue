<template>
  <b-container fluid class="dropList p-0">
    <Item v-for="(item, index) in dropArr" :key='index'
      v-on:updateValue="updateCheck(index)"
      :value="item.value"
      :fonticon="item.font_awesome_icon"
      :checked="item.checked"
      />
  </b-container>
</template>

<script>
import axios from "axios";
import Item from "@/components/Dropdown-item";
import { bus } from "@/main";



export default {
  components: {
    Item
  
    },
  
  data() {
    return {
      dropArr: [],
    }
  },

  props: {
    msg: String
  },

  created() {
    var self = this;
    axios.get('https://api.myjson.com/bins/8vyhc')
    .then(function (response) {
        self.dropArr = response.data;
        console.log(response);
      })
    .catch(function (error) {
        console.log(error);
    });

  },
  computed: {

  },

  methods: {

    //  This function, fired from clicking a list item from the Dropdow-item component, iterates through the dropArr
    //  to find the item that was clicked and then set that item's "checked" property to true
    updateCheck: function(index) {
      
      for(let i = 0; i < this.dropArr.length; i++) {
        if(i == index) {
          this.dropArr[i].checked = true;
        }
        else{
          this.dropArr[i].checked = false;
        } 
      }
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
