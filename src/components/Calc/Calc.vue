<template>
  <div class="card">
    <div class="content">
      <h1 class="title">Calcule seu IMC</h1>
      <Slider 
        inputId="weight" 
        inputName="weight" 
        :maxValue="200" 
        :minValue="0" 
        :stepValue="0.1" 
        label="Peso"
        medida="kg"/>
      <Slider 
        inputId="height" 
        inputName="height" 
        :maxValue="2.5" 
        :minValue="0" 
        :stepValue="0.01" 
        label="Altura"
        medida="m"/>
      <Button :clickFunction="getIMC">Calcular</Button>
      <p id="result">IMC: {{ resultado }}</p>
    </div>
  </div>
</template>

<script>
import Slider from '../Slider/Slider.vue';
import Button from '../Button/Button.vue';
export default {
    name: 'Calc',
    components: { Slider, Button },
    data() {
      return {
        resultado: 'esperando...'
      }
    },
    methods: {
      getIMC() {
        let weight = Number(localStorage.getItem('weight'))
        let height = Number(localStorage.getItem('height'))
        let IMC = weight / (height * height);
        if (IMC < 16) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Baixo peso Grau III).`
        } else if (IMC < 17) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Baixo peso Grau II).`
        } else if (IMC < 18.5) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Baixo peso Grau I).`
        } else if (IMC < 25) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Peso Ideal).`
        } else if (IMC < 30) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Sobrepeso).`
        } else if (IMC < 35) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Obesidade Grau I).`
        } else if (IMC < 40) {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Obesidade Grau II).`
        } else {
          this.resultado = `${IMC.toFixed(1).replace('.', ',')}kg/m² (Obesidade Grau III).`
        }
      }
    }
}
</script>

<style lang="scss" scoped>
@import './Calc.scss';
</style>