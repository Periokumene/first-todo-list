<script setup>
import {ref} from "vue";
import {NH1, NButton, NInput, NSpace, NListItem, NList, NTag, NCheckbox, NP} from 'naive-ui'
const toggleCheck = (todoObject)=>{ todoObject.bDone = !todoObject.bDone;}

defineProps(
    {
      todoObjects: Array
    }
)


</script>

<template>
  <n-space vertical style="width: 900px">
       <n-list hoverable clickable bordered>

         <n-list-item v-for="todoObject in todoObjects">
           <n-space horizontal justify="space-between">
             <n-space>
               <n-checkbox @click="toggleCheck(todoObject)"></n-checkbox>
               <n-p :class="todoObject.bDone ? 'delete' : ''">{{todoObject.Desc}}</n-p>
             </n-space>
             <n-space>
               <n-space>
                 <n-tag :bordered="false" type="info" size="small"> 暑夜 </n-tag>
                 <n-tag :bordered="false" type="info" size="small"> 晚春 </n-tag>
               </n-space>
               <n-space style="width: 70px">
                 <n-tag :bordered type="success" v-if="todoObject.bDone"> Done </n-tag>
                 <n-tag :bordered type="error" v-else> Undone </n-tag>
               </n-space>
             </n-space>
           </n-space>
         </n-list-item>

       </n-list>
  </n-space>
</template>

<style scoped>

.delete
{
  text-decoration: line-through;
}
</style>