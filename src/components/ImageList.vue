<template>
    <ul>
        <li
            v-for="(image, index) in images"
            :key="index"
        >
            <image-block :src="image.src" :title="image.title"/>
            <button @click="remove(index)">Remove</button>
        </li>
    </ul>
    <h4 v-if="images.length === 0">Empty list.</h4>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import ImageBlock from '@/components/ImageBlock.vue';
import { Image } from './type';

export default defineComponent({
    name: 'ImageList',
    props: {
        images: Object as () => Image,
        remove: { type: Function },
    },
    components: {
        ImageBlock,
    },
});

</script>

<style scoped lang="scss">
ul {
    list-style: none;
    padding: 0;

    li {
        display: flex;
        justify-content: space-between;
        outline: 1px solid #f00;
    }

    li + li {
        margin-top: 10px;
    }
}
</style>
