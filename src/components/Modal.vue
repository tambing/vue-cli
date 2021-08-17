<template>
    <!-- @click."modifiers" bisa di gunakan untuk menentukan modifier klik seperti "shift, alt, ctrl, self dll" -->
    <div class="backdrop" @click.self="clickBackdrop">
        <div class="modal" :class="{sale : theme === 'sale'}">
            <h1>{{ dataHead }}</h1>
            <p>{{ content }}</p>
        </div>
    </div>
</template>
<script>
    export default {
        props: ['header', 'content', 'theme'],
        data(){
            return{
                dataHead: this.header
            }
        },
        methods: {
            clickBackdrop(){
                this.$emit('close')
            }
        },
        
    }
</script>
<style scoped>
    /* untuk component style bisa menambahkan "scoped" atau menggunakan nama 
    class yang lebih detail untuk setiap element html */
        /* // componet style */
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop{
        top: 0;
        /* left: 0; */
        position: fixed;
        background: rgba(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }
    h1{
        color: #03cfb4;
        border: none;
        padding: 0;
    }
    p{
        font-style: normal;
    }
    .sale{
        background: crimson;
        color: white;
    }
    .modal.sale h1{
        color: white;
    }
</style>