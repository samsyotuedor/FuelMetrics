<template>
    <div class="container-fluid container-top container-wide bg-dark">
        <div class="container">
            <div class="row">
                <div class="col-md-12 font-weight-bold text-primary">Log In</div>
                <div class="d-flex flex-wrap col-md-12">
                    <div class="col-md-6">
                        <input
                            type="email"
                            v-model="email"
                            class="input"
                            placeholder="Email"
                            required
                            />
                    </div>
                    <div class="col-md-6">
                        <input
                            class="input"
                            v-model="password"
                            type="password"
                            placeholder="Password"
                            required
                            />
                    </div>
                </div>
                <div class="">
                    <button class="btn btn-primary font-weight-bold" @click="Login">Login</button>
                </div>
            
            </div>
        </div>
    </div>
</template>


<script>
import axios from "@/gateway/backendapi";
import {ref } from "vue";
import router from "../../../router/index";
export default {
    setup() {
        const showNav = ref(false);


        const toggleNav = () =>{
            showNav.value = !showNav.value; 
            // menuShouldShow.value = !menuShouldShow.value
        } 

        const Login = () =>{
            let body = {
            email: 'jones_indie@mailinator.com',
            password: 'password123'
            }
            axios.post("/Login",body)
            .then((res)=>{
                console.log(res)
                localStorage.setItem("token", res.data.token);
                router.push('/driverlist')

            })
            .catch((err) =>{
                console.log(err)
            })
        }

        return{
            Login,
            showNav,
            toggleNav
        }
    },
}
</script>

<style scoped>

 
</style>