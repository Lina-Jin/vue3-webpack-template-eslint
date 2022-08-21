<template>
  <h1 :[attr]="msg" @click="increase">{{count}}</h1> 
  <div v-if="count > 4">4보다 큽니다</div>
  <ul v-if="hasFruit">
    <Fruit v-for="fruit in fruits" :key="fruit" :name="fruit">
      {{fruit}}
    </Fruit>
  </ul>
  <button @click="add">{{msg}}</button>
</template>

<script>
import Fruit from '~/components/Fruit'

export default {
  components: {
    Fruit
  },
  data(){
    return {
      attr: 'class', 
      msg:'hi',
      count: 0,
      fruits: ['Apple', 'Banan', 'Cherry']

    }
  },
  computed:{
    hasFruit(){
      return this.fruits.length > 0
    },
    reversedMessage:{
    get() {                  //reversedMessage가 값을 얻어내는 용도의 로직작성
        return this.msg.split('').reverse().join('')
    },
    set(value) {           //reversedMessage에 실제로 어떠한 값을 할당할 때 어떠한 로직을 동작시킬지에 대한 설정작성
      this.msg =value
    }
    }

  },
  methods: {
    increase(){
          this.count +=1
    },
    add() {
      this.reversedMessage += '!?'
    }
  }
}
</script>

<style>
  h1 {
    font-size: 50px;
    color: royalblue;
  }
</style>