<template>
    <div class="row justify-content-center">
        <div class="col-md-8">
            <form-component @new="addComment"></form-component>
            <br>
            <comment-component
                    v-for="(comment, index) in comments"
                    :key="comment.id"
                    :comment="comment"
                    @update="updateComment(index, ...arguments)"
                    @delete="deleteComment(index)">
            </comment-component>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
          return {
              comments: []
          }
        },
        mounted(){
            axios.get('/comments').then((response) => {
                this.comments = response.data;
            });
        },
        methods: {
            addComment(comment) {
                this.comments.push(comment);
            },
            updateComment(index, comment){
                this.comments[index] = comment;
            },
            deleteComment(index){
                this.comments.splice(index, 1);
            }
        }
    }
</script>

<style scoped>

</style>