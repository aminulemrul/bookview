<template>
    <div class="container">
        <div class="card card-default">
            <div class="card-header d-flex justify-content-between align-items-center">
                <h5>Admin - Book List</h5>
                <router-link class="btn btn-sm btn-primary" :to="{name: 'admin.add-book'}">Add Book</router-link>
            </div>
        </div>
        <div class="card card-default">

            <div class="card-body">
                <bookList></bookList>
            </div>
        </div>
    </div>
</template>

<script>
import bookList from './book-list'
export default {
    mounted() {
        //
    },
    components: {
        bookList
    }
}
</script>
