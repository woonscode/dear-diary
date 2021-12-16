<template>
    <div class="post">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
export default {
    name: "Post",
    props: {
        msg: String
    }
}
</script>