<template>
  <q-page class="bg-brown-1 column">
    <div class="todo-wrapper">
      <h2 class="heading">Todo!</h2>
      <q-input
        @keyup.enter="addTask"
        rounded
        outlined
        v-model="newTask"
        label="Enter a task text"
      />
    </div>

    <q-list>
      <q-item
        class="todo-list__item"
        @click="task.done = !task.done"
        clickable
        v-for="(task, index) in tasks"
        :key="task.id"
        v-ripple
      >
        <q-item-section avatar>
          <q-checkbox
            v-model="task.done"
            checked-icon="check"
            unchecked-icon="square"
            color="primary"
          />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn
            @click.stop="deleteTask(index)"
            round
            color="primary"
            icon="delete"
          />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [
        {
          id: 1,
          title: "Pet a dog",
          done: true,
        },
        {
          id: 2,
          title: "Find a cat",
          done: true,
        },
        {
          id: 3,
          title: "Clean your cat's litter box.",
          done: false,
        },
      ],
    };
  },
  methods: {
    deleteTask(index) {
      this.$q
        .dialog({
          dark: true,
          title: "Confirm",
          message: "Are you sure?",
          cancel: true,
          persistent: true,
        })
        .onOk(() => {
          this.tasks.splice(index, 1);
          this.$q.notify({
            message: "Successfully deleted",
            icon: "warning",
          });
        });
    },
    addTask() {
      this.tasks.push({
        title: this.newTask,
        done: false,
      });
      this.newTask = "";
    },
  },
};
</script>

<style>
.heading {
  display: flex;
  justify-content: center;
  margin-bottom: 15px;
}
.todo-list__item {
  min-height: 60px;
}
.todo-wrapper {
  max-width: 600px;
  width: 100%;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
}
</style>
