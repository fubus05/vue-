<template>
  <div class='main'>
    <div v-for="(element, index) in labelQuiz.slice(a, b)" :key="index">
      {{element.label}}
    </div>

    <div class='fist' v-if = 'a === 0'>
      <div v-for="houseType in typeOfHouse" :key="houseType.id">
        <div><input type="checkbox" v-model="selected" v-bind:value="houseType">{{houseType}}</div>
      </div>
    </div>

    <div class='sec' v-if = 'a === 1'>
        <input type="range" min="0" max="17000" step="0" v-model.number="countRange"> 
        <masked-input type="number" v-model.number="countRange" />
    </div>

    <input type="number" v-model="countRange" v-if = 'a === 2'/>


    <button v-if="a > 0" v-on:click="prev">prev</button>
    <button v-on:click="next">next</button>
  </div> 
</template>

<script>

export default {

  name: 'App',
  data () {
    return{
      counter: 0,

      typeOfHouse: ['Студия','1-комнатная','2-комнатная','3-комнатная'],
      labelQuiz: [
        {
          label: 'Какой тип квартиры вас интересует?',
        },
        {
          label: 'Стоимость квартиры',
        },
        {
          label: 'Найдены квартиры по вашему запросу',
        },
      ],
    
      a:0,
      b:1,
      selected: [],
      countRange: 0,
      MaskedInput
    }
  },
  methods: {
    next(){this.a++; this.b++;},
    prev(){this.a--; this.b--;},
  },
  computed: {
      total: function () {
      return this.value * 10
    },
  },
  components: {
    MaskedInput
  }
}
</script>

<style lang="scss">
.main{
    width: 320px;
    height: 607.35px;
    background: #F7AB0D;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-right: -50%;
    transform: translate(-50%, -50%);
    align-items: center;
    justify-content: center
}
</style>
