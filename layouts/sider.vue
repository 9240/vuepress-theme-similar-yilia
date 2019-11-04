<template>
	<div id="sider" style="position:fixed;left:0;top:0;width:300px;">
		<div class="bg-dark" style="height:180px;"></div>
		<a href="/" >
			<img class="img-thumbnail" style="width:120px;height:120px;border-radius:50%;margin-left:90px;margin-top:-60px;" src="http://litten.me/assets/blogImg/litten.png" alt="">
		</a>
		<h3 class="text-center" style="line-height:80px;text-muted">litter</h3>
		<p class="text-center text-muted">胆小认生,不易相处</p>
		<p class="text-center pt-3">主页</p>
		<p class="text-center pb-3">随笔</p>
		<p class="text-center text-muted small">
			<span>所有文章</span>
			<span>/</span>
			<span>友链</span>
			<span>/</span>
			<span>关于我</span>
		</p>
	</div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.min.css';
import '../styles/index.css'
import Sider from './sider';
export default {
	name:'Sider'
}
</script>

<style>
ul{
  list-style: none outside none;
}
</style>