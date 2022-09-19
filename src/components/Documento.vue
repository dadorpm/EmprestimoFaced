<template>
  <div class="principal">
    <table>
      <tr>
        <td>
          <img class="imgufba" alt="ufba logo" src="../assets/UFBA.jpg">
        </td>
        <td class="titulo"><span>{{ titulo }}</span><br><span class="unidade">{{ subtitulo }}</span></td>
        <td>
          <img alt="faced logo" src="../assets/faced.png">
        </td>
      </tr>
    </table>
    <h3 class="h3">Termo de Emprestimo de Equipamentos</h3>
    <table class="dados">
      <tr>
        <td>
          Nome: {{ nome }}
        </td>
      </tr>
      <tr>
        <td>
          Siape/CPF: {{ siapecpf }}
        </td>

      </tr>
      <tr>
        <td>
          Setor/Unidade: {{ setor }}
        </td>
      </tr>
      <tr>
        <td>
          Especificação de Equipamento: {{ equipamento }}
        </td>
      </tr>
    </table>
    <br>
    <div class="responsabilidade">
      <p>Pelo presente Termo de Entrega e Responsabilidade, o servidor acima qualificado declara que recebeu o
        equipamento e acessório
        acima especificados, de propriedade do setor/unidade: {{origem}}, assumindo o compromisso de
        manter a
        guarda pessoal sobre os mesmos, ficando a seu cargo:
      </p>
      <ul>
        <li>Adequada utilização, de acordo com as recomendações;</li>
        <li>Comprometer-se a não conceder empréstimo ou confiar a outrem;</li>
        <li>Comunicar, imediatamente, qualquer incidente e ocorrência com o equipamento sob sua guarda e
          responsabilidade;</li>
        <li>Indenizar os danos causados por negligência, imprudência, imperícia, má utilização, guarda inadequada, desleixo ou outro dano que
          possa decorrer, direta ou indiretamente, de sua ação ou omissão.</li>
      </ul>
    </div>
    <div class="assinatura">
      <br>
      <span>Salvador, </span>{{ dataAtual }}
      <br><br><br>
      <span> Assinatura: </span>
      <span>________________________________________</span>

    </div>
  </div>
</template>

<script>

export default {
  name: 'EmprestimoEquipamento',
  props: {
    titulo: String,
    subtitulo: String,
    nome: String,
    setor: String,
    siapecpf: Number,
    equipamento: String,
    origem: String
  },
  computed: {
    dataAtual() {
      let hoje = new Date()
      let data_formatada = hoje.toLocaleDateString('pt-BR', {
        day: 'numeric',
        month: 'long',
        year: 'numeric',

      })
      return data_formatada

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.pricipal {}

img {
  width: 70px;
  height: 40px;
  margin: 0 70px;
}

.dados {
  margin: 0 50px;
  max-width: 500px;
}

.h3 {
  margin-top: 20px;
  margin-left: 120px;
  margin-bottom: 30px;
}

.imgufba {
  width: 40px;
  height: 60px;
}

.titulo {
  font: 400 12px bold;
  font-family: Arial, Helvetica, sans-serif;
}

.responsabilidade {
  font: 400 12px;
  font-family: Arial, Helvetica, sans-serif;

  margin-left: 50px;
  max-width: 500px;

}
.unidade{
  padding-left: 18px;
}
.assinatura {
  font: 400 12px;
  font-family: Arial, Helvetica, sans-serif;

  margin-left: 50px;
  max-width: 500px;
}
</style>
