<template lang="">
    <input v-model="nuevaTarea" />
    <button @click="agregarTarea">agregar</button>
    <ul>
        <li v-for="tarea in tareas">{{ tarea }}</li>
    </ul>
</template>
<script>
export default {
    data() {
        return {
            nuevaTarea: "",
            tareas: [],
        };
    },
    methods: {
        agregarTarea() {
            const nuevaTarea = this.nuevaTarea;
            this.tareas.push(nuevaTarea);
            this.nuevaTarea = "";
        },
    },
}
</script>
<style lang="">
    
</style>