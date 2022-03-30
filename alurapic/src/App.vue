<template>
  <div>
    <h1>{{ titulo }}</h1>

    <ul>
      <li v-for="foto of fotos" v-bind:key="foto">
        <img v-bind:src="foto.url" v-bind:alt="foto.titulo">
      </li>
    </ul>

    <!--
      também pode ser escrito da seguinte maneira
      <h1 v-text="titulo"></h1>
    -->
    <!--
      <img v-bind:src="foto.url" v-bind:alt="foto.titulo">
      a linha acima pode ser resumida a seguinte:
      <img :src="foto.url" :alt="foto.titulo">
    -->
  </div>
</template>

<script>
export default {

  data() {
    return {
      titulo: 'AluraPic',
      fotos: []
      /*
      fotos: [
        {
          url: 'https://www.petelegante.com.br/dicas/wp-content/uploads/2018/07/ado%C3%A7%C3%A3o-de-cachorro-filhote-750x400.jpg',
          titulo: 'cachorrinho olhando para a câmera'
        },
        {
          url: 'https://www.petlove.com.br/dicas/wp-content/uploads/2018/03/bigodes-de-gato-2-1.jpg',
          titulo: 'gatinho olhando para a câmera'
        },
        {
          url: 'https://www.portaldospassaros.com.br/wp-content/uploads/2018/10/2310_canto-da-calopsita-1000x516.jpg',
          titulo: 'calopsita empoleirada em um galho'
        }
      ]
      */
    }
  },

  created() {
    /*
    // jeito feio de fazer
    let promise = this.$http.get('http://localhost:3000/v1/fotos');
    promise.then(res => {
      res.json().then(fotos => this.fotos = fotos);
    });
    */

    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, erro => console.log(erro));
  }

}
</script>

<style>

</style>
