<template>
  <TodoList>
    <TodoItem v-for="(item, i) in list" :key="i" :title="message"></TodoItem>
  </TodoList>
  {{ time }}
  <p>这个是采用了 vue 的的缩写的方式</p>
  <input :valeu="message" @input="handleChange" />

  <button v-on:[eventName]="cutomEvent">click me</button>
  <br />

  <form>
    <input :value="123" />
    <button v-on:submit.prevent="submitHandler">submit</button>
  </form>

  <br />
  <p>watch 案例</p>
  <div id="watch-example" class="demo">
    <p>
      Ask a yes/no question:
      <input v-model="question" />
    </p>
    <p>{{ question }}</p>
  </div>

  <br />
  <p>class 绑定</p>
  <div :class="[classA, classB]"></div>

  <br />
  <template v-if="awesome">
    <span>这里是 v-if</span>
  </template>
  <div v-else>
    这里是 v-else
  </div>

  <br />
  <div v-show="isShow">
    这里是 v-show
  </div>
  <br />
  <span>vue -for </span>
  <div v-for="(item, index) of list" :key="index">
    {{ item.title }}
  </div>
  <button @click="addItem">在中间增加一个</button>

  <br />
  {{ searchText }}
  <p>fuzujiankaishi</p>
  <Custom v-model="searchText">wojiucaole</Custom>

  <p>自定义简单的 vuex</p>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TodoList from "./components/TodoList.vue";
import TodoItem from "./components/TodoItem.vue";
import Custom from "./components/Custom.vue";
@Options({
  components: {
    TodoItem,
    TodoList,
    Custom,
  },

  data() {
    return {
      message: "hello world",
      list: [
        { title: "lesson1", del: false },
        { title: "lesson2", del: false },
        { title: "lesson3", del: false },
      ],
      time: new Date().getTime(),
      eventName: "click",
      number: 0,
      question: 1,
      classA: "class-A",
      classB: "class-B",
      awesome: false,
      isShow: true,
      searchText: "123",
    };
  },

  methods: {
    handleChange(e: Event) {
      console.log(e);
      this.message = (e.target as HTMLInputElement).value;
    },
    cutomEvent() {
      console.log("123");
    },
    submitHandler() {
      console.log("submit");
    },
    addItem() {
      this.list.splice(1, 1, { title: "lessonNew", del: false });
    },
  },

  beforeCreate() {
    console.log("beforeCreate ");
  },
  create() {
    console.log("creat");
  },
  beforeMount() {
    console.log("beforeMoutted");
  },
  mounted() {
    console.log(new Date().getTime());
  },
  beforeUpdate() {
    console.log("bforeupdate");
  },
  updated() {
    console.log("update");
  },

  watch: {
    // whenever question changes, this function will run
    question() {
      console.log("haha");
    },
  },

  provide() {
    return {
      theme: {
        color: "red",
      },
      background: {
        color: "blue",
      },
      setChildrenRef: (name: any, ref: any) => {
        this[name] = ref;
      },
      getChidlrenRef: (name: any) => {
        return this[name];
      },
      getRef: () => {
        return this;
      },
    };
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
