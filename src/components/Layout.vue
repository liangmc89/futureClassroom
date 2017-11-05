<template>
	<div id="layout">
		<div id="appHeader">
			<mu-appbar title="Title">
				<mu-icon-button icon=":fa fa-bars" slot="left" />
				<mu-flat-button label="expand_more" slot="right" />
				<mu-icon-button icon=":fa fa-chevron-down" slot="right" />
			</mu-appbar>
		</div>
		<div id="appbody">
         <Study></Study>
		</div>
		<div id="appfooter">
			<mu-paper>
				<mu-bottom-nav :value="CurrentMenu" @change="NavChange">
					<mu-bottom-nav-item value="recents" title="首页" icon=":fa fa-home" />
					<mu-bottom-nav-item value="recent" title="学习" icon=":fa fa-book" />
					<mu-bottom-nav-item value="favorites" title="班级" icon=":fa fa-group" />
					<mu-bottom-nav-item value="nearby" title="我的" icon=":fa fa-user" />
				</mu-bottom-nav>
			</mu-paper>
		</div>
	</div>
</template>
<script>
	import Study from "../components/student/study.vue";
	export default {
		name: "Layout",
		data() {
			return {
				CurrentMenu: "recents"
			}
		},
		methods: {
			NavChange: function(val) {
				this.CurrentMenu = val
			}
		},
		components:{
			Study
		}

	}
</script>
<style scoped>
	#layout {
		position: fixed;
		top: 0;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
	
	#appHeader {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
	}
	
	#appfooter {
		position: fixed;
		bottom: 0;
		width: 100%;
		left: 0;
	}
	
	#appbody {
		position: fixed;
		width: 100%;
		top: 56px;
		bottom: 56px;
		
	}
	
	
	@media only screen and (min-width:767px) {
		#appbody {
			top: 64px;
		}
	}
</style>