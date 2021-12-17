<template>
    <div class="container bg-success p-2 border border-5 rounded-3">
        <div class="d-flex justify-content-between pb-1">
            <div class="fs-5 fw-bold text-white">{{ subject }}</div>
            <div>{{ date }}</div>
        </div>
        <div class="border border-info border-4 p-2">{{ message }}</div>
    </div>
</template>

<script>
export default {
    name: "Post",
    props: {
        subject: String,
        message: String,
        date: String,
    }
}
</script>