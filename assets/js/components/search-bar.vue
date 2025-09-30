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
            searchTimeout: null,
        };
    },
    methods: {
        onInput() {
            if (this.searchTimeout) {
                clearTimeout(this.searchTimeout);
            }

            this.searchTimeout = setTimeout(() => {
                this.$emit('search-products', { term: this.searchTerm });
                this.searchTimeout = null;
            }, 200);
        },
    },
};


</script>
