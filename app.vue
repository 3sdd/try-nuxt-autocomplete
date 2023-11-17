<script setup lang="ts">
// @ts-ignore
import autoComplete from "@tarekraafat/autocomplete.js"
import "@tarekraafat/autocomplete.js/dist/css/autoComplete.css"
import data from "@/data.json"

onMounted(()=>{
  const suggestItems=data.data.map(item=>item.name);
  console.log(suggestItems.length)

  const autoCompletejs=new autoComplete({
    selector:'#autoComplete',
    data:{
      src:suggestItems
    },
    placeholder:'検索...',
    threshold:2, // 候補を出し始めるための文字数
    events: {
      input: {
        selection: (event:any) => {
          const selection = event.detail.selection.value;
          console.log(selection)
          autoCompletejs.input.value = selection;
        }
      }
    }

    
  })
})
</script>

<template>
  <div>
    <input type="text" id="autoComplete">
  </div>
</template>
