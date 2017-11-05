<template>
	<!--https://github.com/bedlate/vue-data-loading-->
	<div class="app" id="study">
		<vue-data-loading :loading="loading" :listens="['infinite-scroll', 'pull-down','pull-up']" :init-scroll="true" @pull-up="pullUp" @infinite-scroll="infiniteScroll" @pull-down="pullDown">
			<div slot="infinite-scroll-loading">
				<mu-circular-progress :size="30" :strokeWidth="5" />
			</div>
			<div slot="pull-down-ready">松开刷新数据</div>
			<mu-sub-header>待上课堂</mu-sub-header>
			<swiper :options="swiperOption" ref="mySwiperA">
				<!-- 幻灯内容 -->
				<swiper-slide v-for="(item,index) in courselist" :key="index">
					<CourseItem :courseItem="item" ></CourseItem>
				</swiper-slide>
				

				<!-- 以下控件元素均为可选 -->
				<div class="swiper-pagination" slot="pagination"></div>
				<!--<div class="swiper-button-prev " slot="button-prev "></div>
				<div class="swiper-button-next " slot="button-next "></div>-->
				<!--<div class="swiper-scrollbar " slot="scrollbar "></div>-->
			</swiper>
			<mu-sub-header>历史课堂 </mu-sub-header>

			<transition-group class="datalist" name="flip-list" tag="ul" enter-active-class="animated slideInUp " leave-active-class="animated fadeOutDown ">
				<li v-for="(item, index) in list" :key="index">
					<CourseItem v-bind:courseItem="item"></CourseItem>
				</li>
			</transition-group>

			<div slot="pull-up-loading ">
				<mu-circular-progress :size="30" :strokeWidth="5" />
			</div>
		</vue-data-loading>
	</div>
</template>

<script>
	import VueDataLoading from 'vue-data-loading'
	import { swiper, swiperSlide } from 'vue-awesome-swiper'
	import CourseItem from './CourseItem.vue'
	require('swiper/dist/css/swiper.css')
	export default {
		name: 'app',
		components: {
			VueDataLoading,
			swiper,
			swiperSlide,
			CourseItem
		},
		data() {
			return {

				courselist: [{
					    description:"描述描述",
						title: "大学语文",
						img: "http://occcudapv.bkt.clouddn.com/guchenghu/81773d78-4e4a-40b9-a7e3-33950c85f43c.jpg",
						cdate: "2017-11-5 21:17",
						classroom: "302",
						teacherName: "sdfdfs"
					},
					{   
						description:"描述描述",
						title: "大学语文",
						img: "http://occcudapv.bkt.clouddn.com/guchenghu/81773d78-4e4a-40b9-a7e3-33950c85f43c.jpg",
						cdate: "2017-11-5 21:17",
						classroom: "302",
						teacherName: "sdfdfs"
					},
					{   
						description:"描述描述",
						title: "大学语文",
						img: "http://occcudapv.bkt.clouddn.com/guchenghu/81773d78-4e4a-40b9-a7e3-33950c85f43c.jpg",
						cdate: "2017-11-5 21:17",
						classroom: "302",
						teacherName: "sdfdfs"
					}
				],

				list: [

				],
				loading: false,
				completed: false,
				page: 1,
				swiperOption: {
					// 所有配置均为可选（同Swiper配置）  
					notNextTick: true,
					autoplay: 3000,
					grabCursor: true,
					setWrapperSize: true,
					pagination: '.swiper-pagination',
					paginationClickable: true,
					prevButton: '.swiper-button-prev',
					nextButton: '.swiper-button-next',
					//scrollbar: '.swiper-scrollbar',
					mousewheelControl: true,
					observeParents: true,
					onTransitionStart(swiper) {
						//console.log(swiper)
					}
				}
			}
		},
		methods: {
			fetchData() {
				this.loading = true
				setTimeout(() => {
					//					if(this.page > 3) {
					//						this.completed = true
					//						this.loading = false
					//						return
					//					}
					const temp = [];
					for(let i = this.list.length + 1; i <= this.list.length + 5; i++) {
						var obj = {
							description:"描述描述",
							title: "大学语文",
							img: "http://occcudapv.bkt.clouddn.com/guchenghu/81773d78-4e4a-40b9-a7e3-33950c85f43c.jpg",
							cdate: "2017-11-5 21:17",
							classroom: i.toString(),
							teacherName: "sdfdfs"
						}

						temp.push(obj);
					}
					this.list = this.list.concat(temp)
					this.loading = false
				}, 1000)
			},
			pullUp() {
				this.fetchData()
				this.page++
					console.log("pullup ")
			},
			pullDown() {

				this.list = [];
				this.page = 1;
				this.completed = false;
				this.fetchData();

			},
			infiniteScroll() {
				this.fetchData()
				this.page++
			},
		},
		created() {

		},
		computed: {
			swiper() {
				return this.$refs.mySwiperA.swiper
			}
		},
		mounted() {
			console.log("每次切换都会触发我 ");
			this.swiper.slideTo(3, 1000, false)
		}
		//            this.fetchData()

	}
</script>

<style scoped>
	#study {
		position: static;
		width: 100%;
		margin: 0;
		overflow-x: auto;
		height: 100%;
		text-align: left;
	}
	
	#study .swiper-container {
		padding-bottom: 3em;
	}
	
	#study .loading-header {
		font-size: 1.1em;
	}
	
	#study .loading-footer {
		font-size: 1.1em;
	}
	
	.datalist {
		margin: 0;
		list-style: none;
		text-align: left;
		padding: 0;
		padding-bottom: 1.5em;
	}
	
	.datalist li {
		margin-bottom: 1.5em;
	}
</style>