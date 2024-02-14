<script setup>
import Todolist from "@/components/todolist.vue";
import {ref} from "vue";
import {NButton, NH1, NInput, NSpace} from "naive-ui";

let todoObjects = ref([
  // {bDone: false, Desc: "AAA"},
  // {bDone: false, Desc: "BBB"}
])

const newTaskDesc = ref('');
const pushTask = (inDesc)=>
{
  const inDescNoSpace = inDesc.replaceAll(' ','');
  if (inDescNoSpace.length !== 0)
  {
    todoObjects.value.push({bDone: false, Desc: inDesc})
  }
};

</script>

<template>
  <n-space vertical>
    <n-h1>TODOList</n-h1>
    <n-form-item>
      <n-space>
        <n-input placeholder="New Task" v-model:value="newTaskDesc"/>
        <n-button type="primary" @click="pushTask(newTaskDesc)">Add</n-button>
      </n-space>
    </n-form-item>
    <todolist v-model:todo-objects="todoObjects"/>
  </n-space>
</template>

<style scoped>
</style>
