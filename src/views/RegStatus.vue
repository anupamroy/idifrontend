<template>
    <div>
        <Header/>
        <section class="wrapper bg-light">
			<div class="container py-14 py-md-16">
				
                <div class="row">
					<div class="col-lg-12">
                        <div class="card shadow text-center mx-4">
                            <div class="alert alert-success" v-if="isSuccess">
                                    {{success}}
                            </div>
                            <div class="alert alert-success" v-if="isSuccess">
                                    {{error}}
                            </div>
                        </div>
                    </div>
				</div>
            </div>
        </section> 
        <Footer/>
    </div>
</template>

<script>
    import Header from '@/components/HeaderInner'
    import Footer from '@/components/Footer'
    export default {
        components:{Header,Footer},
        data(){
            return({
                isSuccess:false,
                isError:false,
                success:'',
                error:''
            })
        },
        mounted(){
           const status=this.$route.params.status

           if(status=='success')
           {
               this.isSuccess = true
               this.success = "Thank you for registering with Us. We have sent an email to verify your email"
           }else{
                this.isError = true
                this.error = "Something went wrong. Please check your email for possible reason or contact us"
           }
        }
    }
</script>

<style scoped>

</style>