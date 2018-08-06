<template>
	<transition name="bounce">
		<aside v-show="show">
		<ul @click=handleClick()>
			<router-link to="/matrix" tag="li">Matrix</router-link>
			<li v-for="data in list" @click="addRouter(data)">{{data}}</li>
		</ul>
		<a class="nav-contact-link">寻求合作 | 支持我们</a>
	</aside>
	</transition>	
</template>

<script>
	import router from "../../router"
	export default{
		data() {
			return {
				list:["专题广场","热门文章","应用推荐","生活方式","新玩意"]
			}
		},
		props:["show"],
		methods:{
			handleClick(){
				this.$emit("clickevent");
			},
			addRouter(id){
				router.push(`/tag/${id}`)
			}
		}
	}	
</script>

<style scoped>
	aside{
		position: fixed;
		width: 100%;
		height: 100%;
		top:50px;
		background: white;
		color: #292525;
		z-index: 9;
		overflow: hidden;
	}
	aside ul{
		text-align: center;
		margin-top: 4.375rem;
		padding: 0;
		display: flex;
		flex-flow: row wrap;
	}
	aside ul li{
		width: 50%;
		margin-bottom: 25px;
		list-style: none;
	}
	aside .nav-contact-link{
		display: block;
		width: 100%;
	    text-align: center;
	    margin-top: 200px;
	}

	.bounce-enter-active {
	  animation: bounce-in .5s;
	}
	.bounce-leave-active {
	  animation: bounce-in .5s reverse;
	}
	@keyframes bounce-in {
	  0% {
	    transform:translateZ(-100%);
	    opacity: 0;
	  }
	  100% {
	    transform:translateZ(0px);
	    opacity: 1;
	  }
	}
</style>

