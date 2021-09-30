<template>
    <Header/>
    <section class="wrapper bg-soft-primary">
			<div class="container pt-10 pb-19 pt-md-14 pb-md-22 text-center">
				<div class="row">
					<div class="col-md-10 col-lg-8 col-xl-7 mx-auto">
						<div class="post-header">
							<div class="post-category text-line">
								<a href="#" class="hover" rel="category"></a>
							</div>
							<!-- /.post-category -->
							<h1 class="display-1 mb-3">{{project.projectName}}</h1>
							<p class="lead px-md-12 px-lg-12 px-xl-15 px-xxl-18"></p>
						</div>
						<!-- /.post-header -->
					</div>
					<!-- /column -->
				</div>
				<!-- /.row -->
			</div>
			<!-- /.container -->
		</section>
		<!-- /section -->
		<section class="wrapper bg-light wrapper-border">
			<div class="container pb-14 pb-md-16">
				<div class="row">
					<div class="col-12">
						<article class="mt-n21">
							<figure class="rounded mb-8 mb-md-12"><img :src="baseURL+'/'+projectImages[1]" alt="" /></figure>
							<div class="row">
								<div class="col-lg-10 offset-lg-1">
									<h2 class="display-6 mb-4">About the Project</h2>
									<div class="row gx-0">
										<div class="col-md-9 text-justify">
											<p>{{project.projectDesc}}</p>
										</div>
										<!--/column -->
										<div class="col-md-2 ms-auto">
											<ul class="list-unstyled">
												<li>
													<h5 class="mb-1">Expected Completion Date</h5>
													<p>{{project.expectedDeliveryDate}}</p>
												</li>
												<li>
													<h5 class="mb-1">Project Lead</h5>
													<p>{{project.projectLead}}</p>
												</li>
                                                <li>
													<h5 class="mb-1">Committe Name</h5>
													<p>{{project.committeName}}</p>
												</li>
                                                <li>
													<h5 class="mb-1">Location</h5>
													<p>{{project.projectLocation}}</p>
												</li>
                                                <li>
													<h5 class="mb-1">Address</h5>
													<p>{{project.adderess}}</p>
												</li>
                                                <li>
													<h5 class="mb-1">Local Contact Person</h5>
													<p>{{project.localContactPerson}}</p>
												</li>
											</ul>
											<!-- <a href="#" class="more hover">See Project</a> -->
										</div>
										<!--/column -->
									</div>
									<!--/.row -->
								</div>
								<!-- /column -->
							</div>
							<!--/.row -->
							<div class="row mt-5 gx-md-6 gy-6 light-gallery-wrapper">
								<div class="item col-md-6">
									<figure class="rounded"><img src="src/img/photos/pp2.jpg" alt="" /></figure>
								</div>
								<!--/column -->
								<div class="item col-md-6">
									<figure class="rounded"><img src="src/img/photos/pp3.jpg" alt="" /></figure>
								</div>
								<!--/column -->
								<div class="item col-md-6">
									<figure class="rounded"><img src="src/img/photos/pp4.jpg" alt="" /></figure>
								</div>
								<!--/column -->
								<div class="item col-md-6">
									<figure class="rounded"><img src="src/img/photos/pp5.jpg" alt="" /></figure>
								</div>
								<!--/column -->
							</div>
							<!-- /.row -->
							<div class="row mt-8 mt-md-12">
								<div class="col-md-10 offset-md-1 text-justify">
									<h2 class="mb-4">Quam Mollis Bibendum</h2>
									<p>Maecenas sed diam eget risus varius blandit sit amet non magna. Donec ullamcorper nulla non metus auctor fringilla. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur. Curabitur blandit tempus porttitor. Praesent commodo cursus magna, vel scelerisque nisl consectetur et. Donec id elit non mi porta gravida at eget metus. Donec id elit non mi porta gravida at eget metus. Cras mattis consectetur purus sit amet fermentum.</p>
									<p>Aenean lacinia bibendum nulla sed consectetur. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Maecenas faucibus mollis interdum. Maecenas sed diam eget risus varius blandit sit amet non magna. Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Nulla vitae elit libero, a pharetra augue. Maecenas faucibus mollis interdum etiam porta.</p>
								</div>
								<!-- /column -->
							</div>
							<!-- /.row -->
						</article>
						<!-- /.project -->
					</div>
					<!-- /column -->
				</div>
				<!-- /.row -->
			</div>
			<!-- /.container -->
		</section>
    <Footer/>
</template>

<script>
    import Header from '../components/HeaderInner.vue';
    import Footer from '../components/Footer.vue';
    import axios from 'axios';
    export default {
        components:{Header,Footer},
        data(){
            return({
                baseURL:"http://localhost:3000",
                project:{},
                projectImages:[]
            })
        },
        mounted(){
            const id = this.$route.params.id
            axios.get(this.baseURL+'/api/admin/projects/getprojectbyid/'+id)
            .then(resp=>{
                this.project = resp.data.project
                console.log(this.project)
                const projectImages =resp.data.project.projectImages.split('~')
                projectImages.shift();
                this.projectImages = projectImages

            })
        }
    }
</script>

<style scoped>

</style>