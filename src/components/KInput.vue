<template>
    <div>
        <input type="text" :value="inputValue" @input="handleInput" />
    </div>
</template>

<script>
    export default {
        props: {
            value: {
                type: String,
                default: ''
            }
        },
        data() {
            return {
                inputValue: this.value
            }
        },
        methods: {
            handleInput(e) {
                this.inputValue = e.target.value;
                this.$emit('input', e.target.value);
                
                // 通知父组件做校验
                this.$parent.$emit('validate', this.inputValue);
            }
        },
    }
</script>

<style scoped>

</style>