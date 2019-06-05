<template>
    <div>
        <form>
            <slot></slot>
        </form>
    </div>
</template>

<script>
import { Promise } from 'q';
    export default {
        provide() {
            return {
                form: this
            }
        },
        props: {
            model: {
                type: Object,
                required: true
            },
            rules: {
                type: Object
            }
        },
        methods: {
            async validate(callback) {
                const tasks = this.formItems.map(item => item.validate());
                const results = await Promise.all(tasks);

                callback && callback(results.every(item => !!item));
            }
        },
        created () {
            this.formItems = [];
            this.$on('itemAdd', item => this.formItems.push(item));
        },
    }
</script>

<style scoped>

</style>