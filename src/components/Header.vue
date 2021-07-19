<template>
    <h1 class="text-center text-2xl my-2">{{ msg }}</h1>
</template>

<script>

export default {
    name: "Header",
    props: {
        msg: String
    }
}
</script>