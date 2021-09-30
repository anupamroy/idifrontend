<template>
   <div class="content-wrapper">
         <Header/>
         <section class="wrapper bg-gray">
         <div class="container pt-10 pt-md-14 text-center">
            <div class="row">
              <div class="col-xl-6 mx-auto">
                <h1 class="display-1 mb-4">{{banner.contentHeading}}</h1>
                <p class="lead fs-lg mb-0">{{banner.contentSubHeading}}</p>
              </div>
              <!-- /column -->
            </div>
            <!-- /.row -->
         </div>
			<!-- /.container -->
			<figure class="position-absoute" style="bottom: 0; left: 0; z-index: 2;"><img src="src/img/photos/bg12.jpg" alt="" /></figure>
		</section>
		<!-- /section -->
		<section class="wrapper bg-light angled upper-end lower-end">
			<div class="container py-14 py-md-16">
				<div class="row gx-lg-8 gx-xl-12 gy-10 mb-14 mb-md-17 align-items-center">
					<div class="col-lg-6 position-relative order-lg-2">
						<div class="shape bg-dot primary rellax w-16 h-20" data-rellax-speed="1" style="top: 3rem; left: 5.5rem"></div>
						<div class="overlap-grid overlap-grid-2">
							<div class="item">
								<figure class="rounded shadow"><img :src="baseURL+whoweareImages[0]"  alt=""></figure>
							</div>
							<div class="item">
								<figure class="rounded shadow"><img :src="baseURL+whoweareImages[1]"  alt=""></figure>
							</div>
						</div>
					</div>
					<!--/column -->
					<div class="col-lg-6">
						<img src="src/img/icons/megaphone.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
						<h2 class="display-4 mb-3">{{whoweare.contentHeading}}</h2>
						<p class="lead fs-lg">{{whoweare.contentSubHeading}}</p>
						<div class="mb-6" v-html="whoweare.contentDescription"></div>
					
						<!--/.row -->
					</div>
					<!--/column -->
				</div>
				<!--/.row -->
				<div class="row mb-5">
					<div class="col-md-10 col-xl-8 col-xxl-7 mx-auto text-center">
						<img src="src/img/icons/list.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
						<h2 class="display-4 mb-4 px-lg-14">{{mission.contentHeading}}</h2>
					</div>
					<!-- /column -->
				</div>
				<!-- /.row -->
				<div class="row gx-lg-8 gx-xl-12 gy-10 align-items-center">
				
					<!--/column -->
          <div class="col-lg-6 position-relative order-lg-2">
						
						<div class="lead fs-lg pe-lg-5 text-start" v-html="mission.contentDescription"></div>
						
						
					</div>
          <div class="col-lg-6 position-relative ">
						<div class="shape bg-dot primary rellax w-16 h-20" data-rellax-speed="1" style="top: 3rem; left: 5.5rem"></div>
						<div class="overlap-grid overlap-grid-2">
							<div class="item">
								<figure class="rounded shadow"><img :src="baseURL+whoweareImages[0]"  alt=""></figure>
							</div>
							<div class="item">
								<figure class="rounded shadow"><img :src="baseURL+whoweareImages[1]"  alt=""></figure>
							</div>
						</div>
					</div>
				
					<!--/column -->
				</div>
				<!--/.row -->
			</div>
			<!-- /.container -->
		</section>
		<!-- /section -->
	
	
    <Footer/>
        

  </div>
</template>
<script>
    import Header from '../components/HeaderInner.vue';
    import Footer from '../components/Footer.vue';
    import axios from 'axios'
	
    export default {
      name:'About',
      components:{Header,Footer},
      data(){
        return(
          {
            baseURL:"http://localhost:3000/",
            banner:{},
            whoweare:{},
            whoweareImages:[],
            mission:{},
            missionImages:[]
          }
        )
        

      },
      mounted(){
        let pluginscript = document.createElement('script')
         pluginscript.setAttribute('src','src/js/plugins.js');
         document.head.appendChild(pluginscript)
         let initiatecript = document.createElement('script')
         initiatecript.setAttribute('src','src/js/scripts.js');
         document.head.appendChild(initiatecript)

         axios.get("http://localhost:3000/api/admin/pagecontent/listcontent/60e7d6dacdb5dc3e140b5378")
         .then(resp=>{
            //console.log(resp);
          const bannerArr = resp.data.pageContent.filter(content=>content.sectionName=='banner')
          this.banner = bannerArr[0];

          const whoweareArr = resp.data.pageContent.filter(content=>content.sectionName=='who-we-are-about')
          this.whoweare = whoweareArr[0];
          this.whoweareImages = whoweareArr[0].contentImage.split('~')
          //console.log(this.whoweareImages);
          this.whoweareImages.shift()

          const missionArr = resp.data.pageContent.filter(content=>content.sectionName=='mission-vision')
          this.mission = missionArr[0];


         
         })
      }

    }
</script>
