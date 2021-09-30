<template>
  <div>
      <div class="content-wrapper">
         <Header/>
          <div class="hero-slider-wrapper bg-dark">
              <div class="hero-slider owl-carousel dots-over" data-nav="false" data-dots="true" data-autoplay="true">
                  <div class="owl-slide d-flex align-items-center bg-overlay bg-overlay-400" v-bind:style="{ 'background-image': 'url(http://localhost:3000/' + slider.contentImage + ')' }"  v-for="(slider,index) in sliders" v-bind:key="index">
                      <div class="container" v-bind:class="[(index > 0)? 'light-gallery-wrapper':'']">
                          <div class="row">
                              <div class="col-md-10 offset-md-1 col-lg-7 offset-lg-0 col-xl-6 col-xxl-5 text-center text-lg-start">
                                  <h2 class="display-1 fs-56 mb-4 text-white animated-caption" data-anim="animate__slideInDown" data-anim-delay="500">{{slider.contentHeading}}</h2>
                                  <p class="lead fs-23 lh-sm mb-7 text-white animated-caption" data-anim="animate__slideInRight" data-anim-delay="1000">{{slider.contentHeading}}</p>
                                  <div class="animated-caption" data-anim="animate__slideInUp" data-anim-delay="1500"><a href="#" class="btn btn-lg btn-outline-white rounded-pill">Read More</a></div>
                              </div>
                              <!--/column -->
                          </div>
                          <!--/.row -->
                      </div>
                      <!--/.container -->
                  </div>
                  <!--/.owl-slide -->
                  
              </div>
              <!--/.hero-slider -->
          </div>

          <section class="wrapper bg-light angled lower-end">
              <div class="container py-14 py-md-16">
                  <div class="row gx-lg-8 gx-xl-12 gy-10 mb-14 mb-md-17 align-items-center">
                      <div class="col-lg-6 position-relative order-lg-2">
                          <div class="shape bg-dot primary rellax w-16 h-20" data-rellax-speed="1" style="top: 3rem; left: 5.5rem"></div>
                          <div class="overlap-grid overlap-grid-2">
                              <div class="item">
                                  <figure class="rounded shadow"><img :src="baseURL+welcomeImage[0]" srcset="src/img/photos/about2@2x.jpg 2x" alt=""></figure>
                              </div>
                              <div class="item">
                                  <figure class="rounded shadow"><img :src="baseURL+welcomeImage[1]" srcset="src/img/photos/about3@2x.jpg 2x" alt=""></figure>
                              </div>
                          </div>
                      </div>
                      <!--/column -->
                      <div class="col-lg-6">
                          <img src="src/img/icons/megaphone.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
                          <h2 class="display-4 mb-3">{{welcome.contentHeading}}</h2>
                          <p class="lead fs-lg">{{welcome.contentSubHeading}}</p>
                          <div class="mb-6" v-html="welcome.contentDescription"></div>
                          
                          <!--/.row -->
                      </div>
                      <!--/column -->
                  </div>
                  <!--/.row -->
                  <div class="row mb-5">
                      <div class="col-md-10 col-xl-8 col-xxl-7 mx-auto text-center">
                          <img src="src/img/icons/list.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
                          <h2 class="display-4 mb-4 px-lg-14">{{about.contentHeading}}</h2>
                      </div>
                      <!-- /column -->
                  </div>
                  <!-- /.row -->
                  <div class="row gx-lg-8 gx-xl-12 gy-10 align-items-center">
                      <div class="col-lg-6 order-lg-2">
                          <div class="card me-lg-6">
                              <div class="card-body p-6">
                                  <div class="d-flex flex-row">
                                      <div>
                                          <span class="icon btn btn-circle btn-lg btn-soft-primary disabled me-4"><span class="number">01</span></span>
                                      </div>
                                      <div>
                                          <h2 class="mb-1">{{about_01.contentHeading}}</h2>
                                          <p class="mb-0">{{about_01.contentSubHeading}}</p>
                                      </div>
                                  </div>
                              </div>
                              <!--/.card-body -->
                          </div>
                          <!--/.card -->
                          <div class="card ms-lg-13 mt-6">
                              <div class="card-body p-6">
                                  <div class="d-flex flex-row">
                                      <div>
                                          <span class="icon btn btn-circle btn-lg btn-soft-primary disabled me-4"><span class="number">02</span></span>
                                      </div>
                                      <div>
                                        <h2 class="mb-1">{{about_02.contentHeading}}</h2>
                                          <p class="mb-0">{{about_02.contentSubHeading}}</p>
                                      </div>
                                  </div>
                              </div>
                              <!--/.card-body -->
                          </div>
                          <!--/.card -->
                          <div class="card mx-lg-6 mt-6">
                              <div class="card-body p-6">
                                  <div class="d-flex flex-row">
                                      <div>
                                          <span class="icon btn btn-circle btn-lg btn-soft-primary disabled me-4"><span class="number">03</span></span>
                                      </div>
                                      <div>
                                          
                                        <h2 class="mb-1">{{about_03.contentHeading}}</h2>
                                          <p class="mb-0">{{about_03.contentSubHeading}}</p>
                                      </div>
                                  </div>
                              </div>
                              <!--/.card-body -->
                          </div>
                          <!--/.card -->
                      </div>
                      <!--/column -->
                      <div class="col-lg-6">
                          <h2 class="display-4 mb-3">{{about.contentSubHeading}}</h2>
                          <div class="mb-2" v-html="about.contentDescription"></div>
                          <a href="#" class="btn btn-primary rounded-pill mb-0">Learn More</a>
                      </div>
                      <!--/column -->
                  </div>
                  <!--/.row -->
              </div>
              <!-- /.container -->
          </section>

          <section class="wrapper bg-soft-primary">
              <div class="container pt-16 pb-14 pb-md-0">
                  <div class="row gx-lg-8 gx-xl-0 align-items-center">
                      <div class="col-md-5 col-lg-4 offset-lg-1 d-none d-md-flex position-relative">
                          <div class="shape rounded-circle bg-pale-primary rellax w-21 h-21" data-rellax-speed="1" style="top: 7rem; left: 1rem"></div>
                          <figure><img src="src/img/photos/co1.png" srcset="src/img/photos/co1@2x.png 2x" alt=""></figure>
                      </div>
                      <!--/column -->
                      <div class="col-md-7 col-lg-6 col-xl-6 col-xxl-5 offset-xl-1">
                          <div class="basic-slider owl-carousel dots-start gap-small mt-6" data-margin="30">
                              
                              <div class="item" v-for="(testimonial,index) in testimonials" :key="index">
                                  <blockquote class="icon fs-lg">
                                      <span v-html="testimonial.contentDescription"></span>
                                      <div class="blockquote-details">
                                          <div class="info ps-0">
                                              <h5 class="mb-1">{{testimonial.contentHeading}}</h5>
                                              <p class="mb-0">{{testimonial.contentSubHeading}}</p>
                                          </div>
                                      </div>
                                  </blockquote>
                              </div>
                             
                          </div>
                          <!-- /.owl-carousel -->
                      </div>
                      <!--/column -->
                  </div>
                  <!--/.row -->
              </div>
              <!-- /.container -->
          </section>
          <!-- /section -->
          <section class="wrapper bg-light">
              <div class="container py-14 py-md-16">
                  <div class="row mb-3">
                      <div class="col-md-10 col-xl-9 col-xxl-7 mx-auto text-center">
                          <img src="src/img/icons/team.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
                          <h2 class="display-4 mb-3 px-lg-14">Our Team</h2>
                      </div>
                      <!--/column -->
                  </div>
                  <!--/.row -->
                  <div class="position-relative">
                      <div class="shape rounded-circle bg-soft-yellow rellax w-16 h-16" data-rellax-speed="1" style="bottom: 0.5rem; right: -1.7rem;"></div>
                      <div class="shape rounded-circle bg-line red rellax w-16 h-16" data-rellax-speed="1" style="top: 0.5rem; left: -1.7rem;"></div>
                      <div class="carousel owl-carousel gap-small" data-margin="0" data-dots="true" data-autoplay="false" data-autoplay-timeout="5000" data-responsive='{"0":{"items": "1"}, "768":{"items": "2"}, "992":{"items": "3"}, "1400":{"items": "4"}}'>
                          <div class="item" v-for="(team,index) in teams" :key="index">
                              
                              <div class="item-inner">
                                  <div class="card">
                                      <div class="card-body">
                                          <img class="rounded-circle w-15 mb-4" :src="baseURL+team.contentImage.split('~').pop()    " srcset="src/img/avatars/te1@2x.jpg 2x" alt="" />
                                          <h4 class="mb-1">{{team.contentHeading}}</h4>
                                          <div class="meta mb-2">{{team.contentSubHeading}}</div>
                                          
                                          <nav class="nav social mb-0">
                                              <a href="#"><i class="uil uil-twitter"></i></a>
                                              <a href="#"><i class="uil uil-facebook-f"></i></a>
                                              <a href="#"><i class="uil uil-dribbble"></i></a>
                                          </nav>
                                          <!-- /.social -->
                                      </div>
                                      <!--/.card-body -->
                                  </div>
                                  <!-- /.card -->
                              </div>
                              <!-- /.item-inner -->
                          </div>
                          <!-- /.item -->
                         
                          
                      </div>
                      <!-- /.owl-carousel -->
                  </div>
                  <!-- /.position-relative -->
              </div>
              <!-- /.container -->
          </section>
          <!-- /section -->
          <section class="wrapper bg-soft-primary angled lower-start">
              <div class="container py-14 py-md-16">
                  <div class="row">
                      <div class="col-xl-10 mx-auto">
                          <div class="row align-items-center counter-wrapper gy-6 text-center">
                              <div class="col-md-3">
                                  <img src="src/img/icons/check.svg" class="svg-inject icon-svg icon-svg-lg text-primary mb-3" alt="" />
                                  <h3 class="counter">10+</h3>
                                  <p>Completed Projects</p>
                              </div>
                              <!--/column -->
                              <div class="col-md-3">
                                  <img src="src/img/icons/user.svg" class="svg-inject icon-svg icon-svg-lg text-primary mb-3" alt="" />
                                  <h3 class="counter">2000+</h3>
                                  <p>Proud Members</p>
                              </div>
                              <!--/column -->
                              <div class="col-md-3">
                                  <img src="src/img/icons/briefcase-2.svg" class="svg-inject icon-svg icon-svg-lg text-primary mb-3" alt="" />
                                  <h3 class="counter">1000+</h3>
                                  <p>Share Holders</p>
                              </div>
                              <!--/column -->
                              <div class="col-md-3">
                                  <img src="src/img/icons/award-2.svg" class="svg-inject icon-svg icon-svg-lg text-primary mb-3" alt="" />
                                  <h3 class="counter">1 Bn</h3>
                                  <p>Share Capital</p>
                              </div>
                              <!--/column -->
                          </div>
                          <!--/.row -->
                      </div>
                      <!-- /column -->
                  </div>
                  <!-- /.row -->
              </div>
              <!-- /.container -->
          </section>
          <!-- /section -->
          <section class="wrapper bg-light">
              <div class="container pt-19 pb-14 pt-md-20 pb-md-16">
                  <div class="row gx-md-8 gx-xl-12 gy-10 align-items-center">
                      <div class="col-md-8 col-lg-6 offset-lg-0 col-xl-5 offset-xl-1 position-relative">
                          <div class="shape bg-dot primary rellax w-17 h-21" data-rellax-speed="1" style="top: -2rem; left: -1.4rem;"></div>
                          <figure class="rounded"><img src="src/img/photos/about4.jpg" srcset="src/img/photos/about4@2x.jpg 2x" alt=""></figure>
                      </div>
                      <!--/column -->
                      <div class="col-lg-6">
                          <img src="src/img/icons/telemarketer.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
                          <h2 class="display-4 mb-8">{{contact.contentHeading}}</h2>
                          <div class="d-flex flex-row">
                              <div>
                                  <div class="icon text-primary fs-28 me-6 mt-n1"> <i class="uil uil-location-pin-alt"></i> </div>
                              </div>
                              <div>
                                  <h5 class="mb-1">Address</h5>
                                  <address>Moonshine St. 14/05 Light City, <br class="d-none d-md-block" />London, United Kingdom</address>
                              </div>
                          </div>
                          <div class="d-flex flex-row">
                              <div>
                                  <div class="icon text-primary fs-28 me-6 mt-n1"> <i class="uil uil-phone-volume"></i> </div>
                              </div>
                              <div>
                                  <h5 class="mb-1">Phone</h5>
                                  <p>00 (123) 456 78 90</p>
                              </div>
                          </div>
                          <div class="d-flex flex-row">
                              <div>
                                  <div class="icon text-primary fs-28 me-6 mt-n1"> <i class="uil uil-envelope"></i> </div>
                              </div>
                              <div>
                                  <h5 class="mb-1">E-mail</h5>
                                  <p class="mb-0"><a href="mailto:sandbox@email.com" class="link-body">sandbox@email.com</a></p>
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
          <section class="wrapper bg-soft-primary">
              <div class="container py-14 py-md-16 text-center">
                  <div class="row">
                      <div class="col-md-9 col-lg-7 col-xl-7 mx-auto text-center">
                          <img src="src/img/icons/puzzle-2.svg" class="svg-inject icon-svg icon-svg-md mb-4" alt="" />
                          <h2 class="display-4 mb-3">Join Our Community</h2>
                          <!-- <p class="lead fs-lg mb-6 px-xl-10 px-xxl-15">We are trusted by over 5000+ clients. Join them by using our services and grow your business.</p> -->
                      </div>
                      <!-- /column -->
                  </div>
                  <!-- /.row -->
                  <div class="row">
                      <div class="col-md-6 col-lg-5 col-xl-4 mx-auto">
                          <div class="newsletter-wrapper">
                              <!-- Begin Mailchimp Signup Form -->
                              <div id="mc_embed_signup2">
                                  <form action="https://elemisfreebies.us20.list-manage.com/subscribe/post?u=aa4947f70a475ce162057838d&amp;id=b49ef47a9a" method="post" id="mc-embedded-subscribe-form2" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
                                      <div id="mc_embed_signup_scroll2">
                                          <div class="mc-field-group input-group form-label-group">
                                              <input type="email" value="" name="EMAIL" class="required email form-control" placeholder="Email Address" id="mce-EMAIL2">
                                              <label for="mce-EMAIL2">Email Address</label>
                                              <input type="submit" value="Join" name="subscribe" id="mc-embedded-subscribe2" class="btn btn-primary">
                                          </div>
                                          <div id="mce-responses2" class="clear">
                                              <div class="response" id="mce-error-response2" style="display:none"></div>
                                              <div class="response" id="mce-success-response2" style="display:none"></div>
                                          </div> <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
                                          <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_ddc180777a163e0f9f66ee014_4b1bcfa0bc" tabindex="-1" value=""></div>
                                          <div class="clear"></div>
                                      </div>
                                  </form>
                              </div>
                              <!--End mc_embed_signup-->
                          </div>
                          <!-- /.newsletter-wrapper -->
                      </div>
                      <!-- /column -->
                  </div>
                  <!-- /.row -->
              </div>
              <!-- /.container -->
          </section>
          <!-- /section -->
      </div>
      <Footer/>
  </div>
</template>

<script>
    import Header from '../components/Header.vue';
    import Footer from '../components/Footer.vue';
    import axios from 'axios'
  export default {
      name:'Home',
      components:{Header,Footer},
      data(){
          return({
            baseURL:"http://localhost:3000/",
            sliders:[],
            welcome:{},
            welcomeImage:[],
            about:{},
            about_01:'',
            about_02:'',
            about_03:'',
            testimonials:[],
            teams:[],
            contact:{},
            address:'',
            phone:'',
            email:''
          })
       
      },
      mounted(){
         let pluginscript = document.createElement('script')
         pluginscript.setAttribute('src','src/js/plugins.js');
         document.head.appendChild(pluginscript)
         let initiatecript = document.createElement('script')
         initiatecript.setAttribute('src','src/js/scripts.js');
         document.head.appendChild(initiatecript)

         axios.get("http://localhost:3000/api/admin/pagecontent/listcontent/60e7d66ccdb5dc3e140b536c")
         .then(resp=>{
            this.sliders=resp.data.pageContent.filter(content=>content.sectionName==='slider')
            // this.sliders = resp.data.pageContent.map(slider=>{
            //     slider.contentImage=slider.contentImage.split('~').pop();
            //     slider.contentHeading=slider.contentImage.split('~').pop();
            // })
            this.sliders.forEach(slider=>{
                slider.contentImage = slider.contentImage.split('~').pop()
            })
            // console.log(this.sliders)
            
            const welcomeArr= resp.data.pageContent.filter(content=>content.sectionName==='welcome')
            this.welcome=welcomeArr[0];
            this.welcomeImage = this.welcome.contentImage.split('~');
            this.welcomeImage.shift();
            const aboutArr = resp.data.pageContent.filter(content=>content.sectionName==='about')
            this.about = aboutArr[0];
            this.about_01=aboutArr[1]
            this.about_02 =aboutArr[2]
            this.about_03 =aboutArr[3]
            this.testimonials = resp.data.pageContent.filter(content=>content.sectionName==='testimonial')
            this.teams = resp.data.pageContent.filter(content=>content.sectionName==='team')
            const contactArray = resp.data.pageContent.filter(content=>content.sectionName==='contact')
            this.contact = contactArray[0]
            this.address = contactArray[1]
            this.phone = contactArray[2]
            this.email = contactArray[3]
            console.log(this.contact)
         }
           
            
         )
         .catch(err=>console.log(err))
      }
  }
  
</script>

<style scoped>

</style>