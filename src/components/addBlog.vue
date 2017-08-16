<template>
	<div class="add-blog">
        <h2>Add a New Blog Post</h2>
        <form action="">
            <label for="blog-title">Blog title</label>
            <input type="text" required v-model.lazy="blog.title">
            <label for="blog-content">Blog Content</label>
            <textarea name="blog-content" v-model.lazy="blog.content"></textarea>
            <div class="checkboxes">
                <input type="checkbox" value="ninjas" v-model="blog.categories">
                <label for="">Ninjas</label>
                <input type="checkbox" value="wizards" v-model="blog.categories">
                <label for="">Wizards</label>
                <input type="checkbox" value="mario" v-model="blog.categories">
                <label for="">Mario</label>
                <input type="checkbox" value="cheese" v-model="blog.categories">
                <label for="">Cheese</label>
            </div>
            <button v-on:click.prevent="post">Add Blog</button>
        </form>
        <br>
        <br>
        <transition name="fade">
            <div class="preview" v-if="blog.title || blog.content">
                <h3>Preview Blog</h3>
                <p>Title: {{ blog.title }}</p>
                <p>Content:</p>
                <p>{{ blog.content }}</p>
            </div>    
        </transition>
        
	</div>
</template>



<script>

	export default {
		components: {
		},
		data () {
			return {
                blog: {
                    title: '',
                    content: '',
                    categories: [],
                }
			}
        },
        methods: {
            post() {
                this.$http.post('https://jsonplaceholder.typicode.com/posts', {
                    title: this.blog.title,
                    body: this.blog.content,
                    userId: 1

                }).then(function(data){
                    console.log(data);
                })
            }
        }
	}

</script>



<style lang="scss">
    .add-blog *{
        box-sizing: border-box;
    }

    .add-blog {
        margin: 20px auto;
        max-width: 500px;
    }
    input[type="text"], textarea {
        display: block;
        border: none;
        background-color: #EEE;
        border-radius: 3px;
        padding: 5px;
        width: 100%;
    }


    label {
        display: block;
        margin: 20px 0 10px 
    }

    body {
        padding: 20px;
    }

    .preview {
        border: 2px solid #EEE;
        margin: 30px -30px;
        padding: 10px 30px;
        border-radius: 5px;

    }

    .checkboxes input {
        display: inline-block;
        margin-left: 10px;
        margin-right: 0px;

        &:nth-child(1) {
            margin-left: 0;
        }

    }

    .checkboxes label {
        display: inline-block;
    }

    .fade-enter-active, .fade-leave-active {
        transition: all .2s ease-out;
    }
    .fade-enter, .fade-leave-to {
        opacity: 0;
        transform: translateY(-20px)
    }
</style>
