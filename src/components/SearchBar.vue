<template>
    <div>
        <input @input="onSearch"/>
    </div>
</template>

<script>
    export default{
        name: 'SearchBar',
        methods: {
            onSearch: function(event){
                this.$emit('searchInputChanged', event.target.value);
            }
        }
    };
</script>

<style>

</style>

