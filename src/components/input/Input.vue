<template>
    <div>
        <label for="">{{label}}</label> <br>
        <input :type="type" :placeholder="placeHolder">
    </div>
</template>

<script>
export default {
    name: 'Input',
    props:{
        label: {type: String, require},
        placeHolder: {type: String},
        type: {type: String, default:'text'}
    },
    data(){
        return{

        }
    }
}
</script>