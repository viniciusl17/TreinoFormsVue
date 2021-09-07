<template>
 <div id="app">
   <h1>Fazer Cadastro</h1>
   <form @submit.prevent="enviar">
    <label>Nome </label>
    <input type="text" v-model="user.nome" /><br/>
    
    <label>Email </label>
    <input type="email" v-model="user.email" /><br/>
    
    <label>Data </label>
    <input type="date" v-model="user.dataEvento" /><br/>
    
    <label>Qtd Usuários</label>
    <input type="number" v-model="user.qtdUser" /><br/>
    
    <label>Descrição</label>
    <textarea v-model="descricao"></textarea><br/>
    
    <label>Tecnologias</label>    
        <span><input type="checkbox" value="javascript" v-model="tecnologias" />JavaScript</span>
        <span><input type="checkbox" value="css" v-model="tecnologias"/>Css</span>
        <span><input type="checkbox" value="vuejs" v-model="tecnologias"/>VueJS</span> <br/>
    
    <label>Status do Inventário</label>
    <select v-model="itemSelecionado">
     <!--  --> <option v-for="item in status" :key="item.id" :value="item.nome"> {{item.nome}} </option> <!-- Chama o item onde tem o código -->      
    </select> <br/>

    <label>Categoria</label>
    <span><input type="radio" value="Categoria 1" v-model="categoria" /> Categoria 1</span>
    <span><input type="radio" value="Categoria 2" v-model="categoria" /> Categoria 2</span>
    <span><input type="radio" value="Categoria 3" v-model="categoria" /> Categoria 3</span>
    <span><input type="radio" value="Categoria 4" v-model="categoria" /> Categoria 4</span>
    <br/>
      
    <button type="submit">Enviar</button>
  </form>
 </div>
<hr/>

 <div class="item" v-show="resultado">
   <h2>Usuário cadastrado</h2>
  <label> Nome: {{user.nome}}</label><br/>
  <label>Email: {{user.email}}</label><br/>
  <label>Data do evento: {{user.dataEvento}}</label><br/>
  <label>Quantos Usuários: {{user.qtdUser}}</label><br/>
  <label>Descrição: {{descricao}}</label><br/>
  <label>Tecnologias usadas: </label>
     <ul>
      <li v-for="tech in tecnologias" :key="tech"> {{tech}} </li>
     </ul><br/>
  <label>Status: {{itemSelecionado}} </label> <br/>
  <label>Categoria do inventário: {{categoria}}</label>
 </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      user:{
      nome: '',
      email: '',
      dataEvento: '',
      qtdUser: '',
      },
      descricao: '', 
      tecnologias:[],
      status: [        
        {id: 1, nome: 'EM ESTOQUE'},
        {id: 2, nome: 'BAIXO ESTOQUE'},
        {id: 3, nome: 'SEM ESTOQUE'},        
      ], 
      itemSelecionado: '',
      categoria: '',
      resultado: false
    }
  },
  methods: {
    enviar(){
      alert("Cadastrado com sucesso!");
      this.resultado = true;      
    }
  }  
};
</script>

<style scoped>

form{
  display: flex;
  flex-direction: column;
}

</style>
