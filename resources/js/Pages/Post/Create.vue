<template>
    <form @submit.prevent="submit">
        <label for="title">Title</label>
        <input type="text" id="title" v-model="form.title" />
        <label for="body">Body</label>
        <input type="text" id="body" v-model="form.body" />
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
import { onMounted } from "vue";
import { useForm } from "@inertiajs/vue3";
const props = defineProps({
  post: {
    type: Object,
    default: null,
  },
  isUpdating: {
    type: Boolean,
    default: false,
  },
});
const form = useForm({
  title: "",
  body: "",
});
const submit = () => (props.isUpdating ? updatePost() : addPost());
const addPost = () => form.post("/posts");
const updatePost = () => form.put(`/posts/${props.post.id}`);
onMounted(() => {
  form.title = props.post.title;
  form.body = props.post.body;
});
</script>
<style scoped>
form {
  max-width: 400px;
  margin: 0 auto;
}

label {
  display: block;
  margin-bottom: 8px;
}

input[type="text"] {
  width: 100%;
  padding: 8px;
  margin-bottom: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button[type="submit"] {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #0056b3;
}
</style>
