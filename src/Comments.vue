<template>
    <div class="container">
        <h1>Comentários</h1>
        <hr>
        
        <input type="text" name="nome" placeholder="Nome" class="form-control" v-model="name">
        <textarea name="comentario" id="cm" cols="30" rows="5" placeholder="Comentário" class="form-control" v-model="message"></textarea>
        <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button> 
        
        <div class="list-group">
            <div class="list-group-item" v-for="(comment, index) in comments" :key="index">
                <span class="comment__author">Autor : <strong>{{comment.name}}</strong></span>
                    <p>Comentário: {{comment.message}}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'componentComment',
        data () {
            return {
                comments: [],
                name: '',
                message: ''
            }
        },
        
        methods: {
            addComment() {
                if (this.name.trim() === '' || this.message.trim() === '') {
                    return;
                }

                this.comments.push({
                    name: this.name,
                    message: this.message
                });

                this.name = '';
                this.message = '';
            },

            removeComment(index) {
                this.comments.splice(index, 1)
            }
        },

        computed: { // interface, visualização //disponibiliza variaveis, valores em si, para renderizar no template, assim como data, porém o DATA esta mais relacionado com o v-model, com a base de dados, API
                /* allComents() {
                     return this.comments.map(comment => ({
                         ...comment,
                         name: comment.name.trim() === '' ? 'Anonimo' : comment.name
                     }))*/
        }
    }   
</script>

<style>
    .form-control {
        background-color: #f0f0f0;
        margin-bottom: 15px;
        border: none;
    }
    
    .btn {
        height: 40px;
        width: 1120px;
        background-color: #002e6b;
        border: none;
        font-weight: 400;
        margin-bottom: 40px;
    }

    .btn.btn-primary:hover {
        background-color: #a9c0f3 !important;
        color: #002e6b;
        font-weight: bold;
        border: none;
        margin-bottom: 40px;
    }

    h1 {
        color:#002e6b ;
        padding-top: 150px;
    }

    hr {
        border: #002e6b solid 1px;
    }

    body {
        background-color: #8f9fff;
    }

</style>
