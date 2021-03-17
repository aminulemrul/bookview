<template>
    <div class="container">
        <div class="card card-default">
            <div class="card-header">Add Book</div>

            <div class="card-body">

                <form autocomplete="off" @submit.prevent="createBook">
                    <div class="form-group">
                        <label for="">Book Title</label>
                        <input type="text" v-model="title" id="" class="form-control" name="title" placeholder="">
                        <span class="help-block" ></span>
                    </div>
                    <button type="submit" class="btn btn-primary">Add</button>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
import axios from "axios";

export default {
    data() {
        return {
            'title': '',
        }
    },
    methods: {
        createBook(){
            this.$http({
                url: 'book',
                method: 'POST',
                data:{title:this.title}
            }).then(res => {
                if(res.data == 'success'){
                    this.$router.push({name: 'admin.book'})
                }else{
                    this.has_error = true
                }

            })
            // let token = axios.defaults.headers.common["X-XSRF-TOKEN"];
            // axios.post('book',{title: this.title},
            //     {
            //     headers: {
            //         Authorization: `Bearer ${token}`
            //             }
            //     }).then(response => {
            //     console.log(response);
            // });
        }
    }
}
</script>
