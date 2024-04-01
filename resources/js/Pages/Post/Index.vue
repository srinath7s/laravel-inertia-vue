<template>
  <div class="container">
    <!-- <h1 class="display-4">Inertia CRUD</h1> -->
    <Link href="posts/create" class="btn btn-primary mb-3">Create new Post</Link>
    <table class="table table-bordered">
      <thead class="thead-dark">
        <tr>
          <th v-for="header in headers" :key="header">{{ header }}</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="post in posts" :key="post.id">
          <td>{{ post.title }}</td>
          <td>{{ post.body }}</td>
          <td class="action-buttons">
            <button @click="deletePost(post.id)" class="btn btn-danger">Delete</button>
            <Link :href="`posts/${post.id}/edit`" class="btn btn-warning">Edit</Link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { Link, useForm } from "@inertiajs/vue3";
import { defineProps } from 'vue';

defineProps({
  posts: {
    type: Array,
    default: () => [],
  },
});

const headers = ["Title", "Body"];

const form = useForm({});

const deletePost = (id) => {
  form.delete(`posts/${id}`);
};
</script>

<style scoped>
/* Styling for the container */
.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 20px;
}

/* Styling for the table */
.table {
  width: 100%;
  border-collapse: collapse;
}

.table th,
.table td {
  padding: 8px;
  border: 1px solid #ddd;
}

.table thead th {
  background-color: #343a40;
  color: #fff;
}

/* Styling for the action buttons */
.action-buttons button {
  margin-right: 8px; /* Adjust the margin to add space between buttons */
}

/* Styling for the buttons */
.btn {
  display: inline-block;
  padding: 8px 16px;
  border: 1px solid transparent;
  border-radius: 4px;
  background-color: #007bff;
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}

.btn:hover {
  background-color: #0056b3;
}

.btn-primary {
  background-color: #007bff;
}

.btn-danger {
  background-color: #dc3545;
}

.btn-warning {
  background-color: #ffc107;
}
</style>
