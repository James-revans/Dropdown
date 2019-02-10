<template>
    <b-row class="create m-0">
      <b-col class="p-1 m-0">
        <p v-bind:title="title" class="title m-0">{{ title }}</p>
      </b-col>
    </b-row>
</template>

<script>
import { bus } from '@/main';

export default {  

  data() {
    return {
      title: 'Create a New Item'
      
    }
  },
  methods: {
    
  },
  created() {
    bus.$on('titleChanged', (data) => {
      this.title = data;
    })

  }
}
</script>

<style lang="scss">
  .create{
    max-width: 300px;
    background: rgb(61, 80, 117);
    border-radius: 3px;
    border-bottom-left-radius: 0px;
    p{
      background: white;
      color: black;
      font-size: 20px;
      border-radius: 5px;

    }
  }

</style>
