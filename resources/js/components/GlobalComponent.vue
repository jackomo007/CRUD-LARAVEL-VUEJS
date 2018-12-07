<template>
    <div class="row justify-content-center">
        <div class="col-md-8">
            <form-component @new="addComment"></form-component>
            <br>
            <comment-component
                    v-for="comment in comments"
                    :key="comment.id"
                    :comment="comment">
            </comment-component>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
          return {
              comments: [{
                  'id': 1,
                  'description': 'algo asi',
                  'created_at': '06/12/2018'
              }]
          }
        },
        methods: {
            addComment(comment) {
                this.comments.push(comment);
            }
        }
    }
</script>

<style scoped>

</style>