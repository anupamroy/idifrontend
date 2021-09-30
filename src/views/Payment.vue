<template>
    <div>
        <Header/>
        <section class="wrapper bg-light">
			<div class="container py-14 py-md-16">
				
                <div class="row">
					<div class="col-lg-10 offset-lg-1 col-xl-8 offset-xl-2">
						<h2 class="display-4 mb-3 text-center">Register to Become Member</h2>
						<p class="lead text-center mb-10"></p>
                        <input type="hidden" id="memberID" :value="memberID">
						<div class="row">
							<div class="col-lg-12 mb-4">
									<div class="alert alert-danger" id="error" style="display:none" ></div>
									<div class="alert alert-success" id="success" style="display:none"></div>
							</div>
						</div>
                        <div class="card shadow">
                            <div class="card-heading">
                                <h3 class="my-6 mx-6 text-start">Payment details for your membership</h3>
                            </div>
                            <div class="card-body">
                                <div class="row">
                                    <div class="col-lg-10 text-start">
                                        <strong>Membership Fee:</strong>
                                    </div>
                                    <div class="col-lg-2 text-end">
                                        <strong>$10.00</strong>
                                    </div>
                                </div>
                                <div class="row">
                                    <div class="col-lg-10 text-start">
                                        <strong>Other Fee:</strong>
                                    </div>
                                    <div class="col-lg-2 text-end">
                                        <strong>$2.00</strong>
                                    </div>
                                </div>
                                <div class="row">
                                    <div class="col-lg-10 text-end">
                                        <strong>Total</strong>
                                    </div>
                                    <div class="col-lg-2 text-end">
                                        <strong>$12.00</strong>
                                    </div>
                                </div>
                                <div class="row">
                                    <div class="col-6"></div>
                                    <div class="col-lg-6" id="paypal-button-container">
                                       
                                    </div>
                                </div>
                            </div>
                        </div>
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
    import Header from '../components/HeaderInner.vue'
    import Footer from '@/components/Footer'
 
    import axios from 'axios'
    //const PayPalButton = paypal.Buttons.driver("vue", window.Vue);
    import { loadScript } from "@paypal/paypal-js";
    export default {
        components:{Header,Footer},

        data(){
            return {
                baseURL:"http://localhost:3000/",
                memberID:this.$route.params.id,
                paymentDetails:{
                    paypalTransactionID:'',
                    transactionStatus:'',
                    transactionAmount:'',
                    currencyCode:'',
                    payerName:'',
                    payerEmail:''
                }
            }
        },
        mounted(){
            //const urlParams = new URLSearchParams(window.location.search);
            console.log(this.$route.params)
            localStorage.setItem("memberID",this.$route.params.id)
            const clientID="AejE1MqVC4RHkHWHTWSfJu3EGDaFLX1xzEa45_Yw-v19JoDmua7K1iMw6QvgYY-pefjmhHCUXKFHtozv"
            loadScript({ "client-id":clientID})
            .then((paypal) => {
                paypal.Buttons(
                    {
                        createOrder: function(data, actions) {
                            // This function sets up the details of the transaction, including the amount and line item details.
                            return actions.order.create({
                            purchase_units: [{
                                amount: {
                                value: '12.00'
                                }
                            }]
                            });
                        },
                    onApprove: function(data, actions) {
                       // console.log("AAA"+document.getElementByID('memberID').value)
                        // This function captures the funds from the transaction.
                        return actions.order.capture().then(function(details) {
                        // This function shows a transaction success message to your buyer.
                        //console.log('Transaction completed by ' + details.);
                        if(details.purchase_units[0].payments.captures[0].status=='COMPLETED'){
                            document.getElementById('success').style.display = "inline"
                            document.getElementById('success').innerText='You have successfully completed the payment and registration. Please check your email'
                        }                           
                        else{
                            document.getElementById('error').style.display ="inline"
                            document.getElementById('error').innerText='Transaction Failed Try again'
                        }
                            
                        axios.post("http://localhost:3000/api/transaction/create",{
                            paypalTransactionID:details.purchase_units[0].payments.captures[0].id,
                            transactionStatus:details.purchase_units[0].payments.captures[0].status,
                            transactionAmount:details.purchase_units[0].payments.captures[0].amount.value,
                            payerName:details.payer.name.given_name,
                            payerEmail:details.payer.email_address,
                            currencyCode:"USD",
                            memberID: localStorage.getItem("memberID")


                        })
                        .then(resp=>{
                            console.log(resp)
                        })
                        });
                    }
                }
                    
                
                ).render("#paypal-button-container");
            })
            .catch((err) => {

                console.error("failed to load the PayPal JS SDK script", err);
            });
        }
       
    }
</script>

<style scoped>

</style>