<template>
  <div class="completed-tasks">
    <div v-if="tasks.length === 0" class="no-tasks-message">
      No tasks completed yet.
    </div>
    <div v-else>
      <div v-for="task in tasks" :key="task.name" class="task-item">  
        <div class="task-details">
          <div class="task-header">
            <div class="task-name">{{ task.name }}</div>
            <div class="task-deadline"><b>{{ task.deadline }}</b></div>
          </div>
          <button @click="markAsDone(task)" class="done-button">Mark as Done</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tasks: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    markAsDone(task) {
      console.log('Mark as done:', task);
      this.$emit('mark-as-done', task); // Emitting event to parent component
    }
  }
};
</script>

<style scoped>
.completed-tasks {
  max-width: 600px;
  margin: 0 auto;
}

.no-tasks-message {
  font-size: 18px;
  text-align: center;
  margin-top: 20px;
  color: #666;
}

.task-item {
  background-color: #f9f9f9;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

.task-details {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.task-name {
  font-size: 24px;
  font-weight: bold;
}

.task-deadline {
  font-size: 16px;
  color: #dd4b39;
}

.done-button {
  padding: 8px 16px;
  border-radius: 8px;
  cursor: pointer;
  margin-left: 10px;
  background-color: #28a745;
  color: #fff;
  border: none;
  transition: background-color 0.3s ease;
}

.done-button:hover {
  background-color: #218838;
}
</style>
