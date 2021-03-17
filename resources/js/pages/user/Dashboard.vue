<template>
    <div class="container">
        <div class="card card-default">
            <div class="card-header">Dashboard - Book List</div>

            <div class="card-body">
                <p v-if="isHidden" class="text-center">Added Successfully !</p>
                <div class="row">

                    <div class="col-md-3" v-for="book in books" v-bind:key="book.id">
                        <div class="card mb-3">
                            <div class="card-body">
                                <h5 class="card-title">{{book.title}}</h5>
                                <p class="card-text">{{book.description}}</p>
                                <form @submit.prevent="favorite(book.id)">
                                    <button class="btn btn-primary">Add Favorite</button>
                                </form>

                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            has_error: false,
            books: null,
            id:'',
            isHidden:false,
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
        },
        favorite(id){
            this.$http({
                url: 'book/favorite',
                method: 'POST',
                data:{id:id}
            }).then(res => {
                if(res.data == 'success'){
                    this.isHidden = true
                }else{
                    this.has_error = true
                }

            })
        }
    }
}
</script>
