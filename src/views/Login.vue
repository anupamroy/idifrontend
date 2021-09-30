<template>
    <div class="content-wrapper">
        <Header/>
       
        <section class="wrapper bg-light">
			<div class="container py-14 py-md-16">
				
                <div class="row">
					<div class="col-lg-10 offset-lg-1 col-xl-8 offset-xl-2">
						<h2 class="display-4 mb-3 text-center">Login</h2>
						<p class="lead text-center mb-10"></p>
						<div class="row">
							<div class="col-lg-12">
									<div class="alert alert-danger" v-if="isError">{{error}}</div>
									<div class="alert alert-success" v-if="isSuccess"><strong>{{success}}</strong></div>
							</div>
						</div>
						<form class="contact-form" @submit="checkLogin">
							<div class="messages"></div>
							<div class="controls">
								<div class="row gx-4">
									
                                    <div class="col-md-12">
										<div class="form-label-group mb-4">
											<input id="form_corporation" type="text" name="email" v-model="formValues.email" class="form-control"  required placeholder="Email"  data-error="Valid email is required.">
											<label for="form_corporation">Email *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-12">
										<div class="form-label-group mb-4">
											<input id="form_corporation" type="password" name="email" v-model="formValues.password" class="form-control" required>
											<label for="form_corporation">Password *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<!-- /column -->
									<div class="col-12 text-center">
										<input type="submit" class="btn btn-primary rounded-pill btn-send mb-3" value="Login" onc>
										<p class="text-muted"><strong>*</strong> These fields are required.</p>
									</div>
                                   
									<!-- /column -->
								</div>
								<!-- /.row -->
							</div>
							<!-- /.controls -->
						</form>
						<!-- /form -->
					</div>
					<!-- /column -->
				</div>
            </div>
        </section>  
        <Footer/>
    </div>
</template>

<script>
    import Header from '../components/HeaderInner.vue';
    import Footer from '../components/Footer.vue';
    import axios from 'axios'
	
	
	
    export default {
        components:{Header,Footer},
        data(){
            return({
                baseURL:"http://localhost:3000/",
				countries:[],
				states:[],
                formValues:{
                    
                    email:'',
                    password:'',
                   

                },
                isError:false,
                isSuccess:false,
                success:'',
                error:''
            }
                
            )
        },
        methods:{
            checkLogin(){
                event.preventDefault();
                axios.post(this.baseURL+"api/membership/checklogin",this.formValues)
                .then(resp=>{
                    if(resp.data.result == 1){
                        localStorage.setItem("userName",resp.data.user.userName)
                        localStorage.setItem("userID",resp.data.user.userID)
                        this.$router.push("myaccount");
                    }                       
                    else{
                        this.isError = true
                        this.error = resp.data.message
                    }

                }).catch(err=>{
                    this.isError = true
                    this.error = err.response.data.message
                })
            }

        },
		mounted(){

			//this.countries = countrycitystate.getCountries()
		}

		
        
    }
</script>

<style scoped>

</style>