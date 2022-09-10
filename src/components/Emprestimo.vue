<template>
  <div id="emprestimo">
    <div class="formulario" v-if="mostrar">
      <img src="../assets/faced.png" alt="logo faced">
      <h1>Termo de Emprestimo - SEI FACED</h1>
      <form>
        <ul>
          <li>
            <label for="nome">Nome:</label>
            <input type="text" id="nome" name="nome" v-model="nome">
          </li>
          <li>
            <label for="siapecpf">Siape ou CPF:</label>
            <input type="number" id="siapecpf" name="siapecpf" v-model="siapecpf">
          </li>
          <li>
            <label for="setor">Setor ou Unidade de Origem:</label>
            <input type="text" id="origem" name="origem" v-model="origem">
          </li>
          <li>
            <label for="setor">Setor ou Unidade de Destino:</label>
            <input type="text" id="setor" name="setor" v-model="setor">
          </li>
          <li>
            <label class="especificacao" for="equipamento">Especificação do Equipamento:</label>
            <textarea id="equipamento" name="equipamento" v-model="equipamento" rows="4" cols="60"></textarea>
          </li>
        </ul>
        <button class="button btn-alert" @click="makepdf">Gerar PDF</button>
      </form>

    </div>
    <Documento v-else titulo="Universidade Federal da Bahia" subtitulo="Faculdade de Educação" :nome="nome"
      :equipamento="equipamento" :siapecpf="siapecpf" :setor="setor" :origem="origem" />
  </div>
</template>

<script>
import Documento from './Documento.vue'
import html2canvas from 'html2canvas'
import jspdf from 'jspdf'
export default {
  name: 'EmprestimoEquipamento',
  components: {
    Documento,

  },
  data() {
    return {
      mostrar: true,
      nome: '',
      siapecpf: '',
      setor: '',
      equipamento: '',
      origem:''
    }
  },
  methods: {
    makepdf() {
      window.html2canvas = html2canvas
      let doc = new jspdf("p", "pt", "a4")
      this.mostrar = false
      doc.html(document.querySelector('#emprestimo'), {
        callback: function (pdf) {
          pdf.save("TermoResponsabilidade.pdf")
          alert("Documento Gerado com Sucesso!!! Escolha a pasta para salvar o documento")
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#emprestimo {
  padding-top: 30px;
  height: 8.4in;
  width: 8.5in;
}
li{
  margin: 15px 10px;

}
input,textarea{
  margin-left: 10px;
}
img{
  width: 200px;
  height: 100px;
}
.formulario{
  text-align: center;
}
ul{
  text-decoration: none;
  list-style: none;
}
input{
  width: 300px;
}
.especificacao{
}
textarea{
  display: block;
  margin: 5px 150px;
}
</style>
