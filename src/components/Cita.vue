<!-- Componenete 'Cita' en el que solo se encuentra el cuadrito con la informacion
sobre la cita agendada, el cuadro cambia de color segun la prioridad del paciente -->

<template>
    <div class="citaAgendada text-center" :style="{ backgroundColor: prioridad }">
        <div>
            <h6 class="m-2">
                <b>Paciente</b>
            </h6>
            <p class="m-1">
                {{ paciente }}
            </p>
        <hr>
            <h6 class="m-1">
                <b>Fecha</b>
            </h6>
            <p class="m-1">
                {{ fecha }}
            </p>
        <hr>
            <h6 class="m-1">
                <b>Hora</b>
            </h6>
            <p class="m-1">
                {{ hora }}
            </p>
        <hr>
            <h6 class="m-1">
                <b>Motivo</b>
            </h6>
            <p class="m-1">
                {{ motivo }}
            </p>
        <button @click="$emit('delete')" class="m-1">Eliminar</button>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'Cita',
        data(){
            return{
            }
        },
        props: ['nombre','fecha','hora','prioridad','motivo'],
    }
</script>

<style scoped>
    .citaAgendada{
        width: 200px;
        border: 1px solid black;
        margin: 5px 10px;
    }
</style>