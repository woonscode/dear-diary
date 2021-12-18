<template>
    <div class="post container bg-success p-2 border border-5 rounded-3 mb-2">
        <div class="d-flex justify-content-between pb-1">
            <div class="fs-5 fw-bold text-decoration-underline">{{ subject }}</div>
            <div>{{ date }}</div>
        </div>
        <div class="border rounded-2 border-light border-4 p-2">{{ message }}</div>
        <div class="d-grid mt-2">
            <button @click="del" class="btn btn-danger fw-bold">Delete</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Post",
    props: {
        subject: String,
        message: String,
        date: String,
    },
    methods: {
        del(post) {
            post.target.parentElement.parentElement.remove()
        }
    }
}
</script>

<style>
.post {
    color: #FFFFFF;
}
</style>