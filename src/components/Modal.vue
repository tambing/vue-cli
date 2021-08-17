<template>
    <!-- @click."modifiers" bisa di gunakan untuk menentukan modifier klik seperti "shift, alt, ctrl, self dll" -->
    <div class="backdrop" @click.self="clickBackdrop">
        <div class="modal" :class="{sale : theme === 'sale'}">
            <slot>Default Content</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
            <!-- <h1>{{ dataHead }}</h1>
            <p>{{ content }}</p> -->
        </div>
    </div>
</template>
<script>
    export default {
        props: ['theme'],
        data(){
            return{
                // dataHead: this.header
            }
        },
        methods: {
            clickBackdrop(){
                this.$emit('close')
            }
        },
        
    }
</script>
<style>
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
    .modal h1{
        color: #03cfb4;
        border: none;
        padding: 0;
    }
    .modal p{
        font-style: normal;
    }
    .sale{
        background: crimson;
        color: white;
    }
    .modal.sale h1{
        color: white;
    }
    .modal .actions{
        text-align: center;
        margin: 30px 0 10px 0;
        color: #333;
    }
    .modal .actions a{
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }
</style>