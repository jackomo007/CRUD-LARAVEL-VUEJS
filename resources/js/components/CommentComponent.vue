<template>
    <div class="card">
        <div class="card-header">Publicado en {{ comment.created_at }}</div>

        <div class="card-body">
            <div class="panel-body">
                <p>{{ comment.description }}</p>
            </div>

            <div class="panel-footer">
                <button class="btn btn-default">Update</button>
                <button class="btn btn-danger">Delete</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['comment'],
        data(){
            return {
            }
        }
    }
</script>
