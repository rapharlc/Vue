<template>
<div class="container">
    <div class="row">
        <div class="col-sm-12">
            <h2 class="titulo">Produtos</h2>
            <hr>
        </div>
    </div>
    <div class="row">
            <div class="col-sm-2">
                <Button :callback="adicionarProduto" value="Adicionar"></Button>
            </div>
    </div>
    <div class="row">
        <div class="col-sm-12">
            <table class="table table-hover"> 
                <thead>
                    <tr>
                        <th>Código</th>
                        <th>Nome</th>
                        <th>Quantidade</th>
                        <th>Valor</th>
                        <th>Data de cadastro</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in produtos" :key="item.id">
                        <td>{{item.id}}</td>
                        <td>{{item.nome}}</td>
                        <td>{{item.quantidadeEstoque}}</td>
                        <td>{{item.valor | real}}</td>
                        <td>{{item.dataCadastro | data}}</td>
                        <td>
                            <i @click="editarProduto()" class="fas fa-pen icone"></i>
                            <i @click="excluirProduto()" class="fas fa-trash icone"></i>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

</div>
    
</template>

<script>
import Button from '@/components/button/Button.vue'
import produtoService from '@/services/produto-service'
import Produto from '@/models/Produto'
import conversorData from '@/utils/conversor-data'
import conversorMonetario from '@/utils/conversor-monetario'
export default {
    name:'ControleDeProdutos',
    components:{
        Button
    },
    data(){
        return{
            produtos: []
        }
    },
    filters:{
        data(data){
            return conversorData.aplicarMascaraDataHoraEmDataIso(data);
        },
        real(valor){
            return conversorMonetario.aplicarMascaraParaRealComPrefixo(valor);
        }
    },
    mounted(){
        this.obterTodosOsProdutos();
    },
    methods:{
        adicionarProduto(){
            this.$router.push({name:"NovoProduto"})
        },
        editarProduto(){
            alert('Aqui vou editar produto')
        },
        excluirProduto(){
            alert('Aqui vou excluir produto')
        },
        obterTodosOsProdutos(){
            produtoService.obterTodos()
            .then(response => {
                this.produtos = response.data.map(p => new Produto(p));
                console.log(this.produtos)
            })
            .catch(error => {
                console.log(error)
            })
        }
        
    },
    
}
</script>

<style scoped>
    h1{
        color: red;
    }
    .icone{
        margin: 5px;
        color: var(--cor-primaria);
        cursor: pointer;
    }
</style>