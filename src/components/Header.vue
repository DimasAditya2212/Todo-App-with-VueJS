<template>
    <header>
        <h1>{{ title }}</h1>
        <Button @btn-click="$emit('showForm')" :text="toggleText ? 'Close' : 'Add Task'" :color="toggleText ? 'green' : 'blue'"/>
    </header>
</template>

<script>
import Button from './Button'

export default {
    name: 'Header',
    // data() {
    //     return{
    //         text: 
    //     }
    // },
    components: {
        Button
    },
    props: {
        title: {
            type: String,
            default: 'hello',
        },
        toggleText: Boolean,
    },
    
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

</style>>
