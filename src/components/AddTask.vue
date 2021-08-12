<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="title" v-model="title" name="title" placeholder="Add Task" required />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
        required
      />
    </div>
    <div class="form-control form-control-check">
      <label for="setReminder">Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" id="setReminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
  export default {
    name: 'AddTask',
    data() {
      return {
        title: '',
        day: '',
        reminder: false
      }
    },
    methods: {
      onSubmit(e) {
        e.preventDefault();

        const newTask = {
          title: this.title,
          day: this.day,
          reminder: this.reminder,
        }

        this.$emit('add-task', newTask);

        // clear the form
        this.title = '';
        this.day = '';
        this.reminder = false;
      }
    }
  }
</script>

<style scoped>
  .add-form {
  margin-bottom: 40px;
  }
  .form-control {
    margin: 20px 0;
  }
  .form-control label {
    display: block;
  }
  .form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
  }
  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 0.25rem;
  }
  .form-control-check label {
    order: 2;
  }
  .form-control-check input {
    order: 1;
    width: fit-content;
    height: 20px;
  }
</style>