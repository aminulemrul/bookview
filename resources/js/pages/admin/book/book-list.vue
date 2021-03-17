<template>
    <div>
        <h3>Books</h3>
        <div class="alert alert-danger" v-if="has_error">
            <p>Error.</p>
        </div>

        <table class="table">
            <tr>
                <th scope="col">Id</th>
                <th scope="col"> Book Name</th>
                <th>Action</th>
            </tr>
            <tr v-for="book in books" v-bind:key="book.id" style="margin-bottom: 5px;">
                <th scope="row">{{ book.id }}</th>
                <td>{{ book.title }}</td>
                <td>
                    <a  href="#" class="btn btn-sm btn-danger">Delete</a>
                </td>
            </tr>
        </table>

    </div>
</template>

<script>
export default {
    data() {
        return {
            has_error: false,
            books: null
        }
    },

    mounted() {
        this.getBooks()
    },

    methods: {
        getBooks() {
            this.$http({
                url: `book`,
                method: 'GET'
            })
                .then((res) => {
                    console.log(res)
                    this.books = res.data.books
                }, () => {
                    this.has_error = true
                })
        }
    }
}
</script>
