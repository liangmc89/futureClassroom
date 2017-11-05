<template>
	<div id="app">
		<transition name="login-transition" enter-active-class="animated bounceInLeft" leave-active-class="animated bounceOutRight">
			<Login v-if="!isLogin" v-on:LoginSuccess="LoginSuccess"></Login>
		</transition>
		<transition name="layout-transition" enter-active-class="animated bounceInLeft" leave-active-class="animated bounceOutLeft">
			<Layout v-if="isLogin"></Layout>
		</transition>

	</div>
</template>

<script>
	import Login from "./components/Login.vue"
	import Layout from "./components/Layout.vue"
	
	export default {
		name: 'app',
		data() {
			return {
				isLogin: false
			}
		},
		components: {
			Login,
			Layout
		},
		methods: {
			LoginSuccess: function() {
				this.isLogin = true;
			}

		}
	}
</script>

<style scoped>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;		
		color: #2c3e50;
		margin-top: 60px;
		overflow: hidden;
	}
</style>