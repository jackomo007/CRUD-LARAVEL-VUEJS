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
                const params= {
                    description : this.description
                };
                this.description = '';

                axios.post('/comments', params).then((response) => {
                    const comment = response.data;
                    this.$emit('new', comment);
                });
            }
        }
    }
</script>

<style scoped>

</style>