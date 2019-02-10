<template>
<b-container fluid class="dropdown">
     <!-- v-bind:title="title" -->
    <Button v-on:click.native="toggleActive" class="dropdown_button"></Button>
    <div class="inactive" v-bind:class="{ hide: !(show) }">
        <List/>
    </div>
    
</b-container>
    
</template>

<script>

import Button from '@/components/Dropdown-button';  
import List from '@/components/Dropdown-list';

export default {
    components: {
        List,
        Button
    },
    data() {
        return {
            show: true,
        }
    },
    methods: {
        toggleActive: function() {
            if (this.show) {
                this.show = false;
            }
            else {
                this.show = true; 
            }
        }
    }
    
}
</script>

<style lang="scss"> 
    .dropdown{
        max-width: 300px;

        .hide{
            display: none;
        }
        
    }
    .dropdown_button{
        :hover {
            cursor: pointer;
        }
    }

</style>

