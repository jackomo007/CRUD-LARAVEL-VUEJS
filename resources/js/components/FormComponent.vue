<template>
    <div class="card">
        <div class="card-header">Comments</div>

        <div class="card-body">
            <form action="" v-on:submit.prevent="newComment()">
                <div class="form-group">
                    <label>Write down here your comment:</label>
                    <input type="text" class="form-control" name="comment" v-model="description">
                </div>
                <button type="submit" class="btn btn-primary">
                    Publish comment
                </button>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                description: ''
            }
        },
        methods: {
            newComment() {
                let comment = {
                    id: 2,
                    description: this.description,
                    created_at: '07/12/2018'
                };
                this.$emit('new', comment);
                this.description = '';
            }
        }
    }
</script>

<style scoped>

</style>