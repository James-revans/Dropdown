<template>
<b-container fluid class="dropdown">
    <Button v-on:click.native="toggleActive" class="dropdown_button"></Button>
    <div v-if="active">
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
            active: false
        }
    },
    methods: {
        toggleActive: function() {
            if (this.active) {
                this.active = false;
            }
            else {
                this.active = true; 
            }
        }
    }
    
}
</script>

<style lang="scss"> 
    .dropdown{
        max-width: 300px;
        
    }
    .dropdown_button{
        :hover {
            cursor: pointer;
        }
    }

</style>

