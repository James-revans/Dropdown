<template>
<b-container fluid class="item_select">
    <b-row v-on:click="updateValue" class="py-2">
        <b-col cols="2">
            <div v-show="checked">
                <font-awesome-icon v-bind:icon="fonticon" class="iconActive"/>
            </div>
        </b-col>
        <b-col cols="10" class="text-left p-0">
            {{ value }}
        </b-col>
    </b-row>
</b-container>
    
</template>

<script>
import { bus } from '@/main';

export default {
    props: ["fonticon", "value", "title", "checked"],
    data() {
        return {
            buttonName: 'title'
        }
    },
    methods: {
        
        //  when a list item is clicked:
        //  the updateValue function is triggered which changes the item's "checked" property to true
        //  it's value is passed up to the button title through the event bus
        
        updateValue: function() {
            
            this.$emit('updateValue');
            
            this.buttonName = this.value;
            bus.$emit('titleChanged', this.value);
            
        }
  },   
}
</script>

<style lang="scss">
    .item_select{
        :hover{
            cursor: pointer;
            background: rgb(61, 80, 117);
            color: white;

        }
        &.iconActive {
            color: black;
        }
    }

</style>

