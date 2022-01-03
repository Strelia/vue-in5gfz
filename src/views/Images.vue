<template>
    <image-form :image="newImage" :add="add" />
    <image-list :images="images" :remove="remove" />
    <button v-if="images.length" @click="saveData">Save</button>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

import ImageList from '@/components/ImageList.vue';
import ImageForm from '@/components/ImageForm.vue';
import { Image } from '@/components/type';

export default defineComponent({
    name: 'Images',
    components: {
        ImageForm,
        ImageList,
    },
    setup() {
        const defaultData: Image[] = [{
            src: 'https://images.unsplash.com/photo-1546587348-d12660c30c50?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NXx8bmF0dXJhbHxlbnwwfHwwfHw%3D&w=1000&q=80',
            title: 'Natural Image',
        }];
        const store = localStorage.getItem('images');
        const imagesData = store ? JSON.parse(store) : defaultData;
        const images = ref<Image[]>(imagesData);

        function saveData() {
            const storageData = JSON.stringify(images.value);
            localStorage.setItem('images', storageData);
        }
        function add(newImage: Image) {
            if (newImage.src) {
                images.value.push({
                    src: newImage.src,
                    title: newImage.title,
                });
            }
            saveData();
        }

        function remove(index: number) {
            images.value.splice(index, 1);
            saveData();
        }

        return {
            images,
            add,
            remove,
            saveData,
        };
    },
});
</script>
