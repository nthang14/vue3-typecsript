<template>
  <div>
    <h5>Test1 list props</h5>
    <div v-for="(test, index) in list" :key="index">
      <p>{{ test.title }}- {{ test.location }}- {{ test.point }}</p>
    </div>
  </div>
</template>
<script lang='ts'>
import { defineComponent, toRefs } from 'vue'
import { PropType } from 'vue'
import Test1 from '@/types/test1'
export default defineComponent({
  props: {
    testProps: {
      required: true,
      type: Array as PropType<Test1[]>
    }
  },
  setup(props) {
    const list = toRefs(props).testProps;
    // assign value props
    return { list }
  },
})
</script>
