<template>
    <ul class="menu">
        <li>
            <a @click="() => this.$router.push({path: '/'})">Dashboard</a>
        </li>
        <li>
            <a @click="() => this.$router.push({path: '/controle-de-produtos'})">Produtos</a>
        </li>
        <li>
            <a @click="() => this.$router.push({path: '/controle-de-clientes'}) ">Clientes</a>
        </li>
        <li>
            <a @click="() => this.$router.push({path: '/login'}) ">Sair</a>
        </li>
    </ul>
</template>

<script>

</script>

<style scoped>
    ul.menu  {
        list-style-type: none;
        color: #fff;
        margin: 0;
        padding: 0;
        overflow: hidden;
        background-color: var(--cor-primaria);
    }
    li{
        float: left;
    }
    li:first-child{
        margin-left: 20px;
    }
    li:last-child{
        float: right;
        margin-right: 10px;
    }
    li  a {
        display: block;
        color: #fff;
        padding: 15px 17px;
        text-align: center;

    }
    li a:hover{
        background-color: var(--cor-secundaria);
        cursor: pointer;
    }
    
</style>