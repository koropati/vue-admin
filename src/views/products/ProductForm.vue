<template>
    <form @submit.prevent="submit">
        <div class="mb-3">
            <v-text-field label="Title" v-model="title"></v-text-field>
        </div>
        <div class="mb-3">
            <v-textarea label="Description" v-model="description"></v-textarea>
        </div>
        <div class="mb-3">
            <v-text-field label="Image" v-model="image"></v-text-field>
        </div>
        <div class="mb-3">
            <v-text-field label="Price" type="number" min="0" v-model="price"></v-text-field>
        </div>
        <v-btn color="primary" type="submit">Save</v-btn>
    </form>
</template>
<script>
import axios from 'axios'
export default {
    name: "ProductForm",
    data() {
        return {
            title: '',
            description: '',
            image: '',
            price: 0.0
        }
    },
    methods: {
        async submit() {
            await axios.post('products', {
                title: this.title,
                description: this.description,
                image: this.image,
                price: parseFloat(this.price)
            })

            await this.$router.push('/products')
        }
    }
}
</script>