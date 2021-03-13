<template>
  <div>
    <h1>{{titulo}}</h1>
    <div>
      <input type="text" placeholder="Nome do Aluno" v-model="nome" @keyup.enter="addAluno()">
      <button class="btn btnInput" @click="addAluno()">Adicionar</button>
    </div>

    <table>
      <thead>
        <th>Matricula</th>
        <th>Nome</th>
        <th>Opções</th>
      </thead>
      <tbody v-if="alunos.length">
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{index+1}}</td>
          <!-- <td>{{aluno.id}}</td> -->
          <td>{{aluno.nome}}</td>
          <td>
            <button class="btn btn_Danger" @click="remover(aluno)">Remover</button>
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
        Nenhum Aluno Cadastrado
      </tfoot>
    </table>

  </div>
</template>

<script>
export default {
  data(){
    return{
      titulo: 'School',
      nome: '',
      alunos: []
    }
  },
  props: {

  },
  methods: {
    addAluno() {
      let _aluno = {
        nome: this.nome
      }
      this.alunos.push(_aluno);
      this.nome = '';
    },
    remover(aluno){
      let indice = this.alunos.indexOf(aluno);
      this.alunos.splice(indice,  1);
    }
  },
}
</script>

<style scoped>
input{
  border: 0px;
  padding: 15px;
  font-size: 1.3em;
  color: #687f7f;
  display: inline;
}

.btnInput{
  border:  0px;
  padding: 15px;
  font-size: 1.3em;
  display: inline;
  background-color: rgb(116, 115, 115);
}

.btnInput:hover{
  padding: 15px;
  margin: 0px;
  border: 0px;
}

tfoot{
  color: #156464;
  font-weight: bold;
  font-family: "Montserrat", sans-serif;
  justify-items: center;
}
</style>
