<template>
  <div class="result">
        <div class="title">{{ results[resultIndex].title }}</div>
        <div class="desc">
            {{ results[resultIndex].desc }}
        </div>
    </div>
</template>

<script>
import { ref, computed } from 'vue';
  export default {
    props: ['totalCorrect', 'results'],
    setup(props){

      const resultIndex = computed(()=>{
        let index = 0;

        props.results.forEach((e, i)=>{
          if(e.min <= props.totalCorrect && e.max >= props.totalCorrect){
            index = i;

          }
        })

        return index
      })

      return { resultIndex }
    }
  }
</script>