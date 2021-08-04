<template>
  <h2>Tipo de Cuenta: {{cuenta}}</h2>
  <h2>Saldo: {{saldo}}</h2>
  <h2>Cuenta: {{ estado ? 'Activa' : 'Desactivada'}}</h2>
  <h3>Servicios</h3>
  <div v-for="(item, index) in servicios" :key="index">{{index+1}} - {{ item }}</div>
  <AccionSaldo
        texto="Aumentar Saldo"
        @accion="aumentarSaldo"
  />
  <AccionSaldo
        texto="Disminuir Saldo"
        @accion="disminuirSaldo"
        :desactivar="desactivar"
   />
</template>

<script>
import AccionSaldo from './AccionSaldo'

export default {
    data() {
       return {
          saldo: 1000,
          cuenta: 'Visa',
          estado: true,
          servicios: ['Giro', 'Abono', 'Transferencias'],
          desactivar: false
       }
    },
    methods: {
        aumentarSaldo(){
            this.saldo = this.saldo + 100;
            this.desactivar = false;
        },
        disminuirSaldo(){
            if(this.saldo === 0){
                this.desactivar = true;
                alert('Saldo Agotado');
            }
            else{
                this.saldo = this.saldo - 100;
            }
        }
    },
    components: {
        AccionSaldo
    }
}
</script>

<style>

</style>