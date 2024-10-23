<!-- Componente 'Doctor' es en el que se ingresara la informacion sobre el paciente
a este componente importamos Cita para mostrar abajo del formulario el cuadro con las citas agendadas. -->

<template>
    <div class="wrapper border my-5">
        <div class="wrapper__titles row m-1 justify-content-center">
            <div class="col-2">
                <!-- Si el nombre es true(Si tiene datos) el color es negrito, de lo contrario es rojito -->
                <h3 class="wrapper__titles--text" :style="{color: nombre ? '#21130d' : '#F20942'}">
                    Paciente
                </h3>
            </div>
            <div class="col-2">
                <h3 class="wrapper__titles--text" :style="{color: fecha ? '#21130d' : '#F20942'}">
                    Fecha
                </h3>
            </div>
            <div class="col-2">
                <h3 class="wrapper__titles--text" :style="{color: hora ? '#21130d' : '#F20942'}">
                    Hora
                </h3>
            </div>
            <div class="col-2">
                <h3 class="wrapper__titles--text" :style="{color: prioridad ? '#21130d' : '#F20942'}">
                    Gravedad
                </h3>
            </div>
            <div class="col-2">
                <h3 class="wrapper__titles--text" :style="{color: motivo ? '#21130d' : '#F20942'}">
                    Motivo
                </h3>
            </div>
        </div>
        <!-- En este div se ingresan los datos -->
        <div class="wrapper__details row m-1 justify-content-center">
            <div class="col-2">
                <input type="text" class="wrapper__details--inputs" v-model="nombre">
            </div>
            <div class="col-2">
                <input type="date" class="wrapper__details--inputs" v-model="fecha">
            </div>
            <div class="col-2">
                <input type="time" class="wrapper__details--inputs" v-model="hora">
            </div>
            <!-- Intente hacerlo de otras formas pero ingresar el codigo de color directamente es mas sencillo -->
            <div class="col-2">
                <select name="priority" id="" v-model="prioridad">
                    <option value="" disabled selected>...</option>
                    <option value="#82f529">Baja</option>
                    <option value="#ebf54d">Media</option>
                    <option value="#ea4519">Alta</option>
                </select>
            </div>
            <div class="col-2">
                <input type="text" class="wrapper__details--inputs" v-model="motivo">
            </div>
        </div>
        <div class="wrapper__button text-center">
            <!-- V-if V-else si las casillas no estan rellenas el boton no puede ser presionado -->
            <button @click="agregarConsulta" class="m-2" v-if="nombre == '' || fecha == '' || hora == '' || prioridad == '' || motivo == ''" disabled>Agregar</button>
            <button @click="agregarConsulta" class="m-2" v-else>Agregar</button>
        </div>
    </div>
    <!-- En esta seccion se mostraran las citas -->
    <section class="listaCitas d-flex flex-row">
        <!-- Un v-for para recorrer el array -->
        <div v-for="(cita, i) in consulta" :key="cita">
            <Cita
                :nombre="cita.nombre"
                :fecha="cita.fecha"
                :hora="cita.hora"
                :prioridad="cita.prioridad"
                :motivo="cita.motivo"
                @delete="consulta.splice(i, 1)"
            />
        </div>
    </section>
</template>
<script>
import Cita from './Cita.vue';
export default {
    name: "Medico",
    components: {
        Cita
    },
    data(){
        return{
            nombre: "",
            fecha: "",
            hora: "",
            prioridad: "",
            motivo: "",
            consulta: []
        }
    },
    // Metodo agregar consulta creando un objeto con todos los datos ingresados y luego dando un push al array consulta
    methods: {
        agregarConsulta(){
            const cita = {
                nombre: this.nombre,
                fecha: this.fecha,
                hora: this.hora,
                prioridad: this.prioridad,
                motivo: this.motivo,
            };
            this.consulta.push(cita);
        }
    }
}
</script>
<style scoped>
</style>