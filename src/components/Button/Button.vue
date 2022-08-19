<template>
    <button class="btn-default" @click="clickFunction">
        <slot>{{ buttonText }}</slot>
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        buttonText: String,
        clickFunction: Function
    }
}
</script>

<style lang="scss" scoped>
@import './Button.scss';
</style>