<template>
 <h1>Counter</h1>
 <p>Initial Value: {{ initialValue }}</p>
 <p>Actual value: {{ count }}</p>
 <p>Triple value: {{ count }}</p>
 <button @click="add">Add</button>
</template>

<script>
import { ref, computed, watch, onMounted } from "vue";

export default {
  name: 'Counter',
  props: {
    initialValue: Number
  },
  setup(props){
    //primeira coisa a ser executada - ANTES do componente
    console.log(props);

    const count = ref(props.initialValue);
    const triple = computed(() => count.value * 3);

    const add = () =>{
      count.value++;
    }
    ;
    watch(count, (newValue, OldValue) => {
        console.log("Old Value: " + OldValue + " New Value: " + newValue);
    });

    onMounted(() => {
      console.log("On mounted")
    });
    return { count, add, triple }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
