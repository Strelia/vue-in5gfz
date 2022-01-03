<template>
    <form @submit.prevent="submit()">
        <label>
            Title:
            <input v-model="title"/>
        </label>
        <label>
            Url:
            <input v-model="src"/>
        </label>
        <div>
            <image-block :src="src" :title="title"/>
        </div>
        <input type="submit" value="Add">
    </form>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ImageBlock from '@/components/ImageBlock.vue';

export default defineComponent({
    name: 'ImageForm',
    props: {
        add: { type: Function },
    },
    components: {
        ImageBlock,
    },
    data() {
        return {
            src: '',
            title: '',
        };
    },
    methods: {
        submit() {
            this.add({
                src: this.src,
                title: this.title,
            });
            this.src = '';
            this.title = '';
        },
    },
});
</script>

<style scoped lang="scss">
form {
    max-width: 700px;

    label {
        display: block;
    }

    label + label {
        margin-top: 10px;
    }
}
</style>
