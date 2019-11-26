<template>
    <iframe id="iframepdf" :src="this.field.thumbnails[0]" width="700" height="700"></iframe>
</template>

<script>
    export default {
        props: ['field'],
    }
</script>