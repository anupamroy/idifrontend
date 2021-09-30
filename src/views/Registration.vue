<template>
    <div class="content-wrapper">
        <Header/>
        <section class="wrapper bg-light">
			<div class="container pt-10 pt-md-14 ">
				<div class="row">
					<div class="col-lg-12 col-xxl-12 text-center">
						<h1 class=" mb-0 mt-10 ">Registration Instruction Goes here</h1>
						<p>
							Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatem esse exercitationem unde provident aspernatur explicabo! Libero reiciendis doloremque corporis facilis temporibus iusto, quod rerum, tenetur, id iste facere nihil illum.
						</p>
						<p>
							Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatem esse exercitationem unde provident aspernatur explicabo! Libero reiciendis doloremque corporis facilis temporibus iusto, quod rerum, tenetur, id iste facere nihil illum.
						</p>
					</div>
					<!-- /column -->
				</div>
				<!-- /.row -->
			</div>
			<!-- /.container -->
		</section>
        <section class="wrapper bg-light">
			<div class="container py-14 py-md-16">
				
                <div class="row">
					<div class="col-lg-10 offset-lg-1 col-xl-8 offset-xl-2">
						<h2 class="display-4 mb-3 text-center">Register to Become Member</h2>
						<p class="lead text-center mb-10"></p>
						<div class="row">
							<div class="col-lg-12">
									<div class="alert alert-danger" v-if="isError">{{error}}</div>
									<div class="alert alert-success" v-if="isSuccess"><strong>{{success}}</strong></div>
							</div>
						</div>
						<form class="contact-form" @submit="createMember">
							<div class="messages"></div>
							<div class="controls">
								<div class="row gx-4">
									<div class="col-md-6">
										<div class="form-label-group mb-4">
											
                                            <select name="title" id="title" class="form-select" v-model="formValues.title">
                                                <option value="">Choose Title*</option>
                                                <option value="Mr.">Mr.</option>
                                                <option value="Mrs.">Mrs.</option>
                                                <option value="Miss">Miss</option>
                                            </select>
											
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<!-- /column -->
									<div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_firstname" type="text" name="firstname" class="form-control" v-model="formValues.firstName" placeholder="Doe" required="required" data-error="Last Name is required.">
											<label for="form_lastname">First Name *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<!-- /column -->
									<div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_middlename" type="text" name="middlename" class="form-control" v-model="formValues.middleName" placeholder="Middle Name"  data-error="Valid email is required.">
											<label for="form_email"> Middle Name</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<!-- /column -->
									<div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_lastname" type="text" name="lastname" class="form-control" v-model="formValues.lastName" placeholder="Last Name" required="required" data-error="Valid email is required.">
											<label for="form_phone">Last Name *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<!-- /column -->
                                    <div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_email" type="email" name="email" class="form-control" v-model="formValues.email" placeholder="Email" required="required" data-error="Valid email is required.">
											<label for="form_email">Email *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_phone" type="phone" name="phone" class="form-control" v-model="formValues.phone" placeholder="Phone" required="required" data-error="Valid email is required.">
											<label for="form_phone">Phone *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-12">
                                        <div class="form-label-group mb-4 text-start">
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="radio" name="inlineRadioOptions" v-model="formValues.gender" id="inlineRadio1" value="male">
                                                <label class="form-check-label" for="inlineRadio1">Male</label>
                                            </div>
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="radio" name="inlineRadioOptions" v-model="formValues.gender" id="inlineRadio2" value="female">
                                                <label class="form-check-label" for="inlineRadio1">Female</label>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="col-md-12">
										<div class="form-label-group mb-4">
											<input id="form_community" type="text" name="community_name" class="form-control" v-model="formValues.community" placeholder="Village/City" required="required" data-error="Valid email is required.">
											<label for="form_community">Autonomous Community Name *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_address" type="text" name="address" class="form-control" v-model="formValues.address" placeholder="Address" required="required" data-error="Valid email is required.">
											<label for="form_address">Address *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-6">
										<div class="form-label-group mb-4">
											<input id="form_village" type="text" name="village_city" class="form-control" v-model="formValues.village"  placeholder="Village/City" required="required" data-error="Valid email is required.">
											<label for="form_village">Village/City *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-6">
										<div class="form-label-group mb-4">
											<select name="country" id="country" class="form-select" v-model="formValues.country"  @change="getStates">
                                                <option value="">Select Country *</option>
												<option v-for="country in countries" :key="country.shortName" :value="country.shortName">
													{{country.name}}
												</option>
                                            </select>
											
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-6">
										<div class="form-label-group mb-4">
											<select name="state" id="state" class="form-select" v-model="formValues.state">
                                                <option value="">Select State *</option>
												<option v-for="(state,index) in states" :key="index" :value="state">{{state}}</option>
                                            </select>
											
											<div class="help-block with-errors"></div>
										</div>
									</div>
                                    <div class="col-md-12">
                                        <div class="form-label-group mb-4 text-start">
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="radio" name="inlineRadioOptionsNew" id="inlineRadio3" v-model="formValues.membershipType"  value="corporate">
                                                <label class="form-check-label" for="inlineRadio1">Corporate</label>
                                            </div>
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="radio" name="inlineRadioOptionsNew" id="inlineRadio4" v-model="formValues.membershipType" value="individual">
                                                <label class="form-check-label" for="inlineRadio1">Individual</label>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="col-md-12">
										<div class="form-label-group mb-4">
											<input id="form_corporation" type="text" name="corporation_name" v-model="formValues.corporationName" class="form-control" placeholder="Village/City"  data-error="Valid email is required.">
											<label for="form_corporation">Corporation Name *</label>
											<div class="help-block with-errors"></div>
										</div>
									</div>
									<!-- /column -->
									<div class="col-12 text-center">
										<input type="submit" class="btn btn-primary rounded-pill btn-send mb-3" value="Submit" onc>
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
	import countrycitystate from 'countrycitystatejson'
	import router  from '../router/index'
	
    export default {
        components:{Header,Footer},
        data(){
            return({
                baseURL:"http://localhost:3000/",
				countries:[],
				states:[],
                formValues:{
                    title:'',
                    firstName:'',
                    middleName:'',
                    lastName:'',
                    email:'',
                    phone:'',
                    gender:'',
                    address:'',
                    village:'',
                    state:'',
                    country:'',
                    community:'',
                    membershipType:'',
                    corporationName:''

                },
                isError:false,
                isSuccess:false,
                success:'',
                error:''
            }
                
            )
        },
        methods:{
            createMember(event){
                    event.preventDefault();
                    axios.post(this.baseURL+"api/membership/register",this.formValues)
                    .then(
                        resp=>{
                            if(resp.data.result==1){
                                this.isSuccess=true;
                                this.isError=false
                                this.success="You have successfully completed the first step of membership"
								const id = resp.data.member._id;
								setTimeout(()=>{
									router.push({name:'Payment',params: { type: this.formValues.membershipType,id:id  }})
								},2000)
								
							}
                        }
                    ).catch(
                        err=>{
							console.log(err.response.data)
                            this.isError=true
                            this.isSuccess=false
                            this.error=err.response.data.message
                        }
                    )

            },
			getStates(e){
				//console.log(e.target.value)
				this.states = countrycitystate.getStatesByShort(e.target.value) 
				//console.log(this.states)
			}

        },
		mounted(){

			this.countries = countrycitystate.getCountries()
		}

		
        
    }
</script>

<style scoped>

</style>