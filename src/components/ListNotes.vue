<template>
  <ol class="task-list">
    <li v-bind:key="note.id" v-for="note in notes">
      <section clss="task-btns">
        <Button @click="onRemove(note.id)" class="button" :text="'remove'" />
        <Button @click="onEdit(note.id)" class="button" :text="'edit'" />
      </section>
      <div class="task-content">
        <div class="task-title">
          <h3 class="title">{{ note.title }}</h3>
        </div>
        <div class="task-desc">
          <p class="description">{{ note.description }}</p>
        </div>
      </div>
    </li>
  </ol>
</template>
<script>
import Button from "./Button.vue";

export default {
  name: "ListNotes",
  components: { Button },
  props: {
    notes: Array,
    onRemove: Function,
    onEdit: Function,
  },
};
</script>

<style scoped>
button:not(:last-child) {
  margin-right: 12px;
}
.task-wr {
  border: 1px solid #e7e8ea;
  background-color: #f8f9fa;
  width: 300px;
  min-height: 300px;
  margin: 15px 15px;
  border-radius: 10px;
}
.task-btns-wr {
  display: flex;
  justify-content: flex-end;
  padding: 5px 0;
  border-bottom: 1px solid #e7e8ea;
}
.edit,
.delete {
  width: 30px;
  height: 30px;
  background: transparent;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

.task-title {
  padding: 0 15px;
}
.task-content {
  padding: 15px;
}

.task-list {
  height: 100%;
  max-width: 1013px;
  margin: 0 auto;
  padding: 0;
  list-style: none;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  overflow: auto;
}
</style>
