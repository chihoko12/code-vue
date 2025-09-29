<template>
    <div>
        <input
            v-model="searchTerm"
            class="form-control"
            placeholder="Search Products..."
            type="search"
            @input="onInput"
        >
        <!-- v-model === :value="searchTerm + @input="searchTerm = $event.target.value" -->
    </div>
</template>

<script>
export default {
    name: 'Searchbar',
    data() {
        return {
            searchTerm: '',
        };
    },
    methods: {
        onInput() {
            this.$emit('search-products', { term: this.searchTerm });
        },
    },
};


</script>
