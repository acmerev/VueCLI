<template>
  <div>
    <h1>Tipo de Cuenta: {{ tipodeCuenta }}</h1>
    <h2>Saldo de la Cuenta: {{ saldo }} PokePeso</h2>
    <h2>Estado : {{ estado ? "Activa" : "Cerrada" }}</h2>
    <div v-for="(item, index) in servicios" :key="index">
      {{ index + 1 }} -- {{ item }}
    </div>
    <AccionesSaldo 
          texto="Abonar Saldo"
          @accion="abonar"
    />
    <AccionesSaldo 
           texto="Retirar Saldo" 
           @accion="retirar"
           :desactivar="desactivar"
           />
  </div>
</template>

<script>
import AccionesSaldo from "./AccionesSaldo.vue";
export default {
  components: {
    AccionesSaldo,
  },
  data() {
    return {
      tipodeCuenta: "Regular",
      saldo: 1000,
      estado: true,
      servicios: ["Abonar", "Retirar", "Transferir", "Consultar Saldo"],
      desactivar: false,
    };
  },
  methods: {
    abonar: function () {
      this.saldo += 100;
      this.desactivar = false;
    },
    retirar: function () {
        if(this.saldo == 0){
        this.desactivar = true;
         alert("Saldo Insufiecinte")
        }else {
      this.saldo -= 100;
    }
    },
    
    transferir: function () {
      this.saldo -= 100;
    },
    consultarSaldo: function () {
      return this.saldo;
    },
  },
};
</script>

<style scoped>
h3 {
  color: #0e0a0a;
  font-family: Arial, Helvetica, sans-serif;
}
</style>