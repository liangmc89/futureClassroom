<template>
	<div class="courseItem">
		<div class="courseImg">
			<mu-card-media :subTitle="courseItem.title">
				<img :src="courseItem.img" />
			</mu-card-media>
		</div>

		<div class="courseInfo">
			<ul class="fa-ul">
				<li>{{courseItem.description}}</li>				
				<li><i class="fa-li fa fa-clock-o"></i>{{courseItem.cdate}}</li>
				<li><i class="fa-li fa fa-home"></i>{{courseItem.classroom}}</li>
				<li><i class="fa-li fa fa-user-o"></i>{{courseItem.teacherName}}</li>				
			</ul>		

		</div>
	</div>
</template>
<script>
	export default {
		name: "courseItem",
		props: ['courseItem'],
		data() {
			return {

			}
		}
	}
</script>
<style scoped>
	.courseItem {
		box-sizing: border-box;
		padding: 0 10px;
		display: flex;
	}
	
	.courseImg {
		width: 45%;
		height: 100%;
	}
	
	.mu-card-media {
		height: 100%;
	}
	
	.mu-card-media img {
		height: 100%;
	}
	
	.courseInfo {
		width: 45%;
		margin-left: 3em;
	}
	
	.courseInfo ul {
		list-style: none;		
		margin: 0;
		font-size: 1.2em;
	}
	
	.courseInfo ul li {
		margin-bottom: .2em;
		color: #9da1a7;
		
	}
	.courseInfo ul li i{
		color: #ed764a;
	}
	@media only screen and (max-width:320px  ) {
		.courseInfo ul{
			font-size: 1em;
		}
	}
	@media only screen and (min-width:415px ) {
		.courseInfo ul{
			font-size: 2em;
		}
		.courseInfo {		
		margin-left: 5em;
	}
	}
</style>