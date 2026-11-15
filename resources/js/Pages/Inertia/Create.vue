<script setup>
    import { reactive } from 'vue';
    import { router, usePage} from '@inertiajs/vue3';

    const page = usePage()

    const form = reactive({
        title: null,
        content: null
    })

    const submitFunction = () => {
        router.post('/inertia', form)
    }
</script>

<template>
    <form @submit.prevent="submitFunction">
        <input type="text" name="title" v-model="form.title"><br>
        <p v-if="page.props.errors.title">{{ page.props.errors.title }}</p>
        <input type="text" name="content" v-model="form.content"><br>
        <p v-if="page.props.errors.content">{{ page.props.errors.content }}</p>
        <button>送信</button>
    </form>
</template>