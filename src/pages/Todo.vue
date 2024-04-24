<template>
  <q-page class="bg-brown-1 column"
    ><h2 class="heading">Todo!</h2>

    <q-list>
      <q-item
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
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
.heading {
  display: flex;
  justify-content: center;
}
</style>
