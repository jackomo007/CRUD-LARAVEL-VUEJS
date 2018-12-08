<template>
    <div class="card">
        <div class="card-header">Created at {{ comment.created_at }} - Updated at {{ comment.updated_at }}</div>

        <div class="card-body">
            <div class="panel-body">
                <input v-if="editMode" type="text" class="form-control" v-model="comment.description">
                <p v-else>{{ comment.description }}</p>
            </div>

            <div class="panel-footer">
                <button v-if="editMode" class="btn btn-default" v-on:click="onClickUpdate()">Update</button>
                <button v-else class="btn btn-default" v-on:click="onClickEdit()">Edit</button>
                <button class="btn btn-danger" v-on:click="onClickDelete()">Delete</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['comment'],
        data(){
            return {
                editMode: false
            }
        },
        methods: {
            onClickDelete(){
                axios.delete(`/comments/${this.comment.id}`).then(() => {
                    this.$emit('delete');
                });
            },
            onClickEdit(){
                this.editMode = true
            },
            onClickUpdate(){
                const params = {
                    description: this.comment.description
                };
                axios.put(`/comments/${this.comment.id}`, params).then((response) => {
                    this.editMode = false
                    const comment = response.data;
                    this.$emit('update', comment);
                });

            }
        }
    }
</script>
