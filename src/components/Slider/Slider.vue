<template>
    <div class="slider">
        <label :for="inputId">{{ label }}</label>
        <span id="weight-value">{{ String(value).replace('.', ',') }}{{ medida }}</span>
        <input type="range" :name="inputName" :id="inputId" :min="minValue" :max="maxValue" :step="stepValue" @input="getValue">
    </div>
</template>

<script>
export default {
    name: 'Slider',
    props: {
        inputName: String,
        inputId: String,
        minValue: Number,
        maxValue: Number,
        stepValue: Number,
        label: String,
        medida: String
    },
    data() {
        return {
            value: 0
        }
    },
    mounted() {
        let el = document.getElementById(this.inputId)
        el.value = localStorage.getItem(this.inputId) ? localStorage.getItem(this.inputId) : this.maxValue / 2 
        this.value = document.getElementById(this.inputId).value
        localStorage.setItem(this.inputId, this.value)
    },
    methods: {
        getValue(e) {
            this.value = e.target.value
            localStorage.setItem(this.inputName, e.target.value)
        }
    }

}
</script>

<style lang="scss" scoped>
@import './Slider.scss';
</style>