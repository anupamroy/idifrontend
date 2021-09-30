<template>
    <div class="content-wrapper">
        <Header/>
        <section class="wrapper bg-light">
			<div class="container pt-10 pt-md-14">
				<div class="row">
					<div class="col-lg-12 col-xxl-12">
						<h1 class="display-1 mb-0 mt-10">Check out some of our awesome projects with creative ideas.</h1>
					</div>
					<!-- /column -->
				</div>
				<!-- /.row -->
			</div>
			<!-- /.container -->
		</section>
		<!-- /section -->
		<section class="wrapper bg-light">
			<div class="container py-14 py-md-16">
				<div class="grid grid-view projects-masonry">
					<!-- <div class="isotope-filter filter mb-10">
						<p>Filter:</p>
						<ul>
							<li><a class="filter-item active" data-filter="*">All</a></li>
							<li><a class="filter-item" data-filter=".concept">Concept</a></li>
							<li><a class="filter-item" data-filter=".product">Product</a></li>
							<li><a class="filter-item" data-filter=".workshop">Workshop</a></li>
							<li><a class="filter-item" data-filter=".still-life">Still Life</a></li>
						</ul>
					</div> -->
					<div class="row gx-md-10 gy-10 gy-md-13 isotope">
						
						<!-- /.project -->
						<div class="project item col-md-6 workshop" v-for="(project,index) in projects" :key="index">
							
							<figure class="lift rounded mb-6"><router-link :to="{name:'Project Detail', params:{id:project._id}}"> <img alt="" :src="baseURL+project.projectImages.split('~').pop()" /></router-link></figure>
							<div class="project-details d-flex justify-content-center flex-column">
								<div class="post-header">
									
									<h3 class="post-title">{{project.projectName}}</h3>
								</div>
								<!-- /.post-header -->
							</div>
							<!-- /.project-details -->
						</div>
						
						<!-- /.project -->
					</div>
					<!-- /.row -->
				</div>
				<!-- /.grid -->
			</div>
			<!-- /.container -->
		</section>
        <Footer/>    
    </div>
</template>

<script>
    import Header from '../components/HeaderInner.vue';
    import Footer from '../components/Footer.vue';
    import axios from 'axios';
    export default {
      
      components:{Header,Footer},
      data(){
		return({
			baseURL:"http://localhost:3000/",
			projects:[],
			projectImages:[]
		})
      },
      mounted(){
        let pluginscript = document.createElement('script')
         pluginscript.setAttribute('src','src/js/plugins.js');
         document.head.appendChild(pluginscript)
         let initiatecript = document.createElement('script')
         initiatecript.setAttribute('src','src/js/scripts.js');
         document.head.appendChild(initiatecript)
         axios.get("http://localhost:3000/api/admin/projects/list")
         .then(resp=>{
             this.projects = resp.data.projects
         })
      }
    }
</script>

<style scoped>

</style>