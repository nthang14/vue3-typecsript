<template>
  <div class="app">
    Hello, world
    <p>My name : {{ name }} - {{ age }}</p>
    <p>Test : {{ test }}</p>
    <div @click="changeName('new name')">change name</div>
    <div @click="changeAge(100)">change age number</div>
    <div @click="changeAge('change age')">change age string</div>
    <div @click="changeTest(10)">change test </div>
    <div>Test methods in setup</div>
    <input type="number" v-model="age" @change="inputNumber">
    <!-- <h5>Test1 array</h5>
    <div v-for="(test, index) in test1" :key="index">
      <p>{{ test.title }}- {{ test.location }}- {{ test.point }}</p>
    </div> -->
    <div>
      <ListProps :testProps="test1" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue';
import Test1 from '@/types/test1'
import ListProps from './components/ListProps.vue'
export default defineComponent({
  name: 'App',
  components: {
    ListProps
  },
  setup() {
    const state = reactive({
      name: 'name',
      age: 0 as number | string
    })
    const test = ref<number>(0);
    const test1 = ref<Test1[]>([
      { 
        title: 'i am test1 - 1.',
        location: 'here',
        point: 5
      },
      { 
        title: 'i am test1 - 2.',
        location: 'here',
        point: 5
      },
      { 
        title: 'i am test1 - 3.',
        location: 'here',
        point: 5
      },
      { 
        title: 'i am test1 - 4.',
        location: 'here',
        point: 5
      }
    ]);
    return { ...toRefs(state), test, test1 };
  },
  // data() {
  //   return {
  //     name: 'Name',
  //     age: 1 as number | string
  //   }
  // },
  methods: {
    changeName(name: string) {
      this.name = name;
    },
    inputNumber() {
      console.log('age: ' + this.age);
    },
    changeAge(age: number | string) {
      this.age = age;
    },
    changeTest (test: number) {
      console.log('test: ' + test + 'typeof = ' + typeof test);
      this.test = test;
    }
  }
});
</script>

<style>
</style>
