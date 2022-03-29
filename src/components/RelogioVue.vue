<template>
  <div class="componente">
    <p class="titulo">QUE HORAS SÃO ?</p>

    <div class="relogio">
      <div class="div">
        <p class="numero">{{ hora }}</p>
        <p class="texto">HORAS</p>
      </div>

      <div class="div">
        <p class="numero">{{ minuto }}</p>
        <p class="texto">MINUTOS</p>
      </div>

      <div class="div segundos">
        <p class="numero segundos">{{ segundo }}</p>
        <p class="texto segundos">SEGUNDOS</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.componente{
  margin-top: -100px;
}
.titulo {
  margin-bottom: 10px;
  letter-spacing: 10px;
  font-weight: bolder;
}
.relogio {
  display: flex;
  justify-content: center;
  flex-direction: row;
  align-items: center;
  text-align: center;
  -webkit-box-reflect: below 0px linear-gradient(transparent, #0004);
}
.div {
  width: 100px;
  margin: 5px 5px 0px 5px;
  background: hsl(204, 100%, 52%);
}
.numero {
  font-size: 60px;
  margin: 10px 0px 20px 0px;
}
.texto {
  padding: 5px 2px;
  background: hsl(204, 93%, 45%);
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5);
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 2px;
}

.segundos{
  background: hsl(308, 93%, 41%);
}
.texto.segundos{
  background: hsl(308, 93%, 34%);

}

@media (max-width: 350px) {
  .relogio {
    flex-direction: column;
  }
}
</style>
<script>
export default {
  name: "RelogioVue",
  data() {
    return {
      hora: "00",
      minuto: "00",
      segundo: "00",
    };
  },
  created() {
    this.iniciarRelogio();
  },
  methods: {
    iniciarRelogio() {
      setInterval(() => {
        let data = new Date();

        this.hora =
          data.getHours().toString().length == 1
            ? "0" + data.getHours().toString()
            : data.getHours().toString();

        this.minuto =
          data.getMinutes().toString().length == 1
            ? "0" + data.getMinutes().toString()
            : data.getMinutes().toString();

        this.segundo =
          data.getSeconds().toString().length == 1
            ? "0" + data.getSeconds().toString()
            : data.getSeconds().toString();

      }, 1000);
    },
  },
};
</script>
