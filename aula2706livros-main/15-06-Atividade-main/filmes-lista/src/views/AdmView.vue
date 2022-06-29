<script>
import { v4 as uuid} from "uuid";
export default {
  data() {
    return {
      novo_Autor: "",
      novo_livro: "",
      nova_editora: "",
      nova_categoria:"",
      Autor: [
        { id: "9a7c7c02-874d-4556-8a13-4a33c56571d1", livro: "Machado de Assis", autor: "69 anos", editora: "", categoria: "1" },
        { id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807", livro: "Jorge Amado",  autor: "88 anos", editora: "" , categoria: "2"},
        { id: "874b37b6-3546-4c05-bc54-5d0fdb886d16", livro: "Monteiro Lobato", autor: "66 anos ", editora: "", categoria: "3" },
        { id: "9b35ce67-a4ec-45a0-be67-1983e37bd723", livro: "Fernando Pessoa",autor: "47 anos ", editora: "", categoria: "4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_Autor !== ""){
      const novo_id=uuid();
      this.Autor.push({
        id: novo_id,
        livro: this.novo_Autor,
        livroid: this.novo_livro,
        editora: this.nova_editora,
        autor: this.nova_categoria,
      });
        this.novo_Autor = "";
        this.novo_livro = "";
        this.nova_editora = "";
        this.nova_categoria = "";
      }
    },
    excluir(Autor){
      const indice = this.Autor.indexOf(Autor);
      this.Autor.splice(indice, 1);
    },
  },
};


</script>
<template>
  <div class="container">
    <div class="title">
    </div>
    <div class="form-input">
      <input type="text" placeholder="livro" v-model="novo_Autor" @keypress.enter="salvar" /> 
      <input type="text" placeholder="autor" v-model="novo_livro" @keypress.enter="salvar" />
      <input type="text" placeholder="editora" v-model="nova_editora" @keypress.enter="salvar" />
      <input type="text" placeholder="categoria" v-model="nova_categoria" @keypress.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Livro</th>
            <th>Autor</th>
            <th>Editora</th>
            <th>Categoria</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="Autor in Autor" :key="Autor.id">
            <td>{{Autor.id}}</td>
            <td>{{Autor.livro}}</td>
            <td>{{Autor.autor}}</td>
            <td>{{Autor.editora}}</td>
            <td>{{Autor.categoria}}</td>
            <td>

              <button @click="excluir(Autor)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style scoped>
.form-input input {
    display: block;
    border-radius: 10px;
    padding: 0 0.5rem;
    height: 40px;
  }
  .form-input button {
    
    height: 40px;
    margin-left: 1%;
    background-color:#FFA67B ;
    font-weight: bold;
    color: white;
    border: 1px solid #FFA67B;
    border-radius: 10px;
    width: 15%;
  }
  
   .list-items {
    display: flex;
    justify-content: left;
    margin: 2rem 0;
  }
  
  table {
    width: 60%;
    border: 1px solid black;
    border-collapse: collapse;
    text-align: center;
    font-size: 1.1rem;
  }
</style>
