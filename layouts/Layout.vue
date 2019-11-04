<template>
    <div id="Layout">
        <div class="h-100" style="width:300px;">
            <Sider />
        </div>
        <div style="background-color:#eaeaea;margin-left:300px;">
            <div class="m-2 bg-white">
                <div class="row justify-content-between ml-0">
                    <div class="pl-5" style="border-left:5px solid black;">
                        <h2 class="pt-3 pb-3 text-muted">{{title}}</h2>
                    </div>
                    <div class="pr-5">
                        <h2 class="pt-3 pb-3 text-muted">{{date.split('T')[0]}}</h2>
                    </div>
                </div>
                <Content class="m-2 pl-5 pr-5"/>
                <hr />
                <div class="row justify-content-between">
                    <div class="pl-5">
                        <span class="bg-info mr-1 p-2 badge" v-for="(tag,index) in tags">{{tag}}</span>
                    </div>
                    <div class="pr-5">
                        <p class="bg-dark p-1">
                            <a href="item.path" style="color:#fff;">分享</a>
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
            date:'',
            tags:[],
            title:''
        }
    },
    components:{
		Sider
	},
    created(){
        this.date = this.$page.frontmatter.date
        this.tags = this.$page.frontmatter.tags
        this.title = this.$page.frontmatter.title
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