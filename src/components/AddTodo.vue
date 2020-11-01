<template>
    <div>
        <!-- NOTE: Prevent default behavior -->
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" name="Submit" class="btn">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo() {
            const newTodo = {
                title: this.title,
                completed: false
            }
            // send up to parents
            this.$emit('add-todo', newTodo);
            // clear form
            this.title = '';
        }
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }
</style>