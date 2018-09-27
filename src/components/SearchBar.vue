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

<style scoped>
    input{
        width: 75%;
    }
    div{
        margin: 20px;
        text-align: center;
    }
</style>

