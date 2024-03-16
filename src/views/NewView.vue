<template>
    <MemoForm :memo="emptyObject" />
</template>

<script>
import MemoForm from '../components/MemoForm.vue'
export default {
    name: 'NewView',
    components: {
        MemoForm
    },
    data() {
        return {
            emptyObject: {}
        }
    }
}
</script>