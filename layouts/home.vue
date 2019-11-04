<template>
    <div id="home">
		<div class="h-100" style="width:300px;">
			<Sider />
		</div>
		<div style="background-color:#eaeaea;margin-left:300px;">
			<div v-for="(item,index) in article" class="bg-white m-2">
				<div class="row justify-content-between ml-0">
					<div class="pl-5" style="border-left:5px solid black;">
						<h2 class="pt-3 pb-3 text-muted">{{item.frontmatter.title}}</h2>
					</div>
					<div class="pr-5">
						<h2 class="pt-3 pb-3 text-muted">{{item.frontmatter.date.split('T')[0]}}</h2>
					</div>
				</div>
				<p v-html="item.excerpt" class="pl-5 pr-5"></p>
				<hr />
				<div class="row justify-content-between">
					<div class="pl-5">
						<span class="bg-info mr-1 p-2 badge" v-for="(tag,index) in item.frontmatter.tags">{{tag}}</span>
					</div>
					<div class="pr-5">
						<p class="bg-dark p-1">
							<a :href="item.path" style="color:#fff;">展开全文</a>
						</p>
					</div>
				</div>
			</div>
		</div>
    </div>
</template>
<script>
import 'bootstrap/dist/css/bootstrap.min.css';
import Sider from './sider';
export default {
	data() {
		return {
		article:[]
		}
	},
	components:{
		Sider
	},
	created(){
		this.article = this.$site.pages.slice(1,this.$site.pages.length)
	}
}
</script>
<style>
a.header-anchor {
  font-size: .85em;
  float: left;
  margin-left: -.87em;
  padding-right: .23em;
  margin-top: .125em;
  opacity: 0;
}
</style>