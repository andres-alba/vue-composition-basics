<template>
  <div class="home">
    <h2 ref="appTitleRef">{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>

    <div>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>
    <p>This counter is {{ oddOrEven }}</p>
    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" v-autofocus />
    </div>
  </div>

  <div class="edit">
    <h4>Edit Counter title:</h4>
    <input v-model="counterData.title" type="text" />
  </div>
</template>

<script setup>
import { ref, reactive, computed, watch, onMounted, nextTick } from 'vue'
import { vAutofocus } from '@/directives/vAutofocus'

const appTitle = 'My counter app'
const appTitleRef = ref(null)

const counterData = reactive({
  count: 0,
  title: '',
})

watch(
  () => counterData.count,
  (newCount, oldCount) => {
    if (newCount === 20) {
      alert('you made it to 20')
    }
  }
)

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return 'even'

  return 'odd'
})

const increaseCounter = async (amount, e) => {
  counterData.count += amount
  await nextTick(() => {
    console.log('do something when counter has updated in the dom')
  })
}
const decreaseCounter = (amount) => {
  counterData.count -= amount
}

onMounted(() => {
  console.log(appTitleRef.value)
})
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  margin: 30px;
}
.edit {
  margin-top: 60px;
}
</style>
