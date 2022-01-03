<template>
    <div class="image">
        <img :src="src" :alt="title" class="img-item__src" />
        <h2 class="img-item__title">{{ title }}</h2>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'ImageBlock',
    props: {
        src: String,
        title: String,
    },
});

</script>

<style scoped lang="scss">
    .image {
        display: flex;
        align-items: center;
        img {
            width: 200px;
            height: auto;
            max-height: 200px;
        }

        h2 {
            margin-left: 20px;
        }
    }
</style>
