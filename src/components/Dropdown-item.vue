<template>
<b-container fluid class="item_select">
    
    <b-row class="py-2">
        <b-col cols="2">
            <div v-if="check">
                <font-awesome-icon v-bind:icon="fonticon"/>
                <!-- <i class="fonticon"></i>
                <i class="fas fa-coffee"></i> -->
            </div>
        </b-col>
        <b-col v-on:click="toggleCheck" cols="8" class="text-left p-0">
            {{ value }}
        </b-col>
        <b-col v-on:click="updateValue" cols="2" class="p-0" style="font-size: 10px; color: white;">
            Update
        </b-col>
    </b-row>
</b-container>
    
</template>

<script>
export default {
    props: ["fonticon", "value"],
    data() {
        return {
            check: false
        }
    },
    methods: {
        toggleCheck: function() {
            if(this.check) {
                this.check = false;
            }
            else {
                this.check = true;
            }

        },
        updateValue: function() {
            this.$emit('updateValue', 'newDropDownValue');
        }
  }
    
}
</script>

<style lang="scss">
    .item_select{
        :hover{
            cursor: pointer;
            background: rgb(61, 80, 117);
            color: white;

        }
    }

</style>

