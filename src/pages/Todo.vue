<template>
  <q-page class="bg-brown-1 column">
    <div class="todo-wrapper">
      <q-input
        class="q-mt-xl"
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
    <div v-if="!tasks.length" class="tasks-empty absolute-center">
      <h4 class="text-primary text-center">TODO is empty</h4>
      <q-img style="max-width: 104px" src="../assets/empty.svg"></q-img>
    </div>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [],
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
      this.tasks.unshift({
        title: this.newTask,
        done: false,
      });
      this.newTask = "";
    },
  },
};
</script>

<style>
.todo-list__item {
  min-height: 60px;
}
.todo-wrapper {
  max-width: 600px;
  width: 100%;
  margin: 0 auto;
}
.tasks-empty {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  opacity: 0.8;
}
</style>
