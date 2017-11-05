<template>
	<div id="login" >
		<div id="appLogo" class="animated fadeInDown">
		<img src="../assets/logo.png">
		<h2>未来教室</h2>
		</div>
		<div class="animated fadeInUp"  >
		<mu-text-field label="用户名" v-model="userName"  type="number" icon=":fa fa-user-o" labelFloat /><br/>
		<mu-text-field label="密码" v-model="passWord"  type="password" labelFloat icon=":fa fa-key" /><br/>
	    <mu-raised-button icon=":fa " @click="login" label="登录" class="demo-raised-button" primary/>
	    </div>
	</div>
</template>
<script>
	export default {
		name:"login",
		data() {
			return {
				userName: "",
				passWord: "",
				Logged: false
			}

		},
		methods:{
			login:function(){
				//登录
				this.Logged=!this.Logged;
				if(this.Logged==true){
					//登录成功
					this.$emit('LoginSuccess');
				}
			    
				
			}
		}
		
	}
</script>
<style>
	#login{
		overflow: hidden;
		position: fixed;
		top:0;
		left:0;
		bottom: 0;
		right: 0;
		width: 100%;
		
	}
	#appLogo{
		margin: 1.5rem 0;
	}

</style>