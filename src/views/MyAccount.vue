<template>
    <div class="content-wrapper">
        <Header/>
        
        <section class="wrapper bg-light ">
			<div class="container py-4 py-md-16">
				
                <div class="row">
					<div class="col-lg-10 offset-lg-1 col-xl-8 offset-xl-2">
						
						
                        
						<div class="card shadow  my-10">
                            <div class="card-header bg-primary text-white text-start">
                                <h3 class="text-white">My Profile</h3>
                            </div>
                            <div class="card-body px-4 py-4">
                                <div class="row">
                                <div class="col-12 text-start">
                                    <h4>Name:</h4>
                                    {{profile.firstName}} {{profile.lastName}}
                                </div>
                               
                            </div>
                            <div class="row my-4">
                               
                                <div class="col-6 text-start">
                                    <h4>Email</h4>
                                    {{profile.email}}
                                </div>
                                <div class="col-6 text-start">
                                    <h4>Phone</h4>
                                    {{profile.phone}}
                                </div>
                            </div>
                            <div class="row my-4">
                                <div class="col-6 text-start">
                                    <h4>Address</h4>
                                    {{profile.address}}<br/>
                                    {{profile.village}}<br/>
                                    {{profile.state}}<br/>
                                    {{profile.state}}<br/>
                                </div>
                                <div class="col-6 text-start">
                                    <h4>Community</h4>
                                    {{profile.community}}
                                </div>
                            </div>
                            </div>
                        </div>
						
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
              
                isError:false,
                isSuccess:false,
                success:'',
                error:'',
                profile:{},
            }
                
            )
        },
    
		mounted(){
                const userID = localStorage.getItem("userID")
                
                axios.post(this.baseURL+"api/membership/profile",{id:userID})
                .then(resp=>{
                    this.profile = resp.data.profile
                }).catch(err=>{
                    console.log(err)
                })
			//this.countries = countrycitystate.getCountries()
		}

		
        
    }
</script>

<style scoped>

</style>