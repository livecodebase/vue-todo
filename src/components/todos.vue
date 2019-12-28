<template>
  <div class="todocont">
    <div
      v-for="todo in todos"
      :key="todo.id"
      class="todoitem"
      v-bind:class="{ completed: todo.completed }"
    >
      <label class="checkmarkcnt">
        <input
          type="checkbox"
          @change="togglecompleate(todo.id)"
          v-bind:checked="todo.completed"
        />
        <span class="checkmark" />
      </label>
      <div class="todo-text">{{ todo.title }}</div>
      <button @click="$emit('deltodo', todo.id)" class="close-btn">
        X
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "todolist",
  data() {
    return {};
  },
  props: ["todos"],

  methods: {
    togglecompleate(id) {
      this.todos.find(todo => {
        if (todo.id === id) {
          todo.completed = !todo.completed;
        }
      });
    }
  }
};
</script>

<style scoped>
.todocont {
  width: 100%;
}
.todoitem {
  background-color: #f2f2f2;
  display: flex;
  align-items: center;
  padding: 20px 50px;
  margin: 10px;
}
/* The checkmarkcnt */
.checkmarkcnt {
  display: block;
  position: relative;
  padding-left: 35px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.checkmarkcnt input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: rgb(170, 170, 170);
  margin-top: -12px;
}

/* On mouse-over, add a grey background color */
.checkmarkcnt:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.checkmarkcnt input:checked ~ .checkmark {
  background-color: #2196f3;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.checkmarkcnt input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.checkmarkcnt .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
.todo-text {
  font-size: 17px;
  font-weight: 500;
  margin-left: 10px;
}
.close-btn {
  margin-left: auto;
  padding: 5px;
  font-size: bold;
  color: #fff;
  background-color: rgb(236, 78, 78);
  border: 0;
  cursor: pointer;
}
.close-btn:focus {
  outline: none;
}
.completed {
  background-color: #fff;
}
.completed div {
  text-decoration: line-through;
}
</style>
