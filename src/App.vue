<template>
	<div>
		<add-blog>
			
		</add-blog>
	</div>
</template>



<script>

import addBlog from './components/addBlog.vue'

export default {
	components: {
		"add-blog": addBlog 
	},
	data () {
		return {

		}
	}
}

</script>



<style lang="scss">
	body {
		font-family: Roboto, Segoe UI, -apple-system
	}
</style>
