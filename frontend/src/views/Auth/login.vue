<template>
<div>

    <div class="login-main-section">
        <div class="lms-wrapper">
            <h2 class="lg-title">Login</h2>
            <div class="login-container">
                <div class="login-content">
                    <form @submit.prevent="authStore.loginUser(loginDetails)">

                        <div class="email-container">
                            <label for="email">Email</label>
                            <input v-model="loginDetails.email" id="email" name="email" required placeholder="" class="user-email" type="email">
                        </div>
                        
                        <div class="password-container">
                            
                            <div class="password-wrapper">
                                <label for="passcode-input">Password</label>
                                <div class="password-input">
                                    <input v-model="loginDetails.password" name="password" required id="passcode-input" placeholder="" class="user-password" type="password">
                                </div>
                            </div>
                        </div>
                        <div class="login-button-wrapper">
                            <button type="submit">log in</button>
                            
                        </div>
                    </form>
                    <p>Don't have an account? <RouterLink to="/register">Sign up.</RouterLink> </p>
                </div>
            </div> 
        </div>
    </div>


</div>
</template>

<script setup lang="ts">

import LoadingScreen from '@/components/LoadingScreen.vue';
import { ref } from 'vue';
import {useAppStore} from '@/stores/state'

const authStore = useAppStore()


/**user details to be used to log them in */
const loginDetails = ref({
    email: "",
    password: ""
})

</script>

<style scoped lang="scss">



.login-main-section{
    margin:0 auto;
    height: calc(100vh - 8rem);
    max-width: var(--maxWidth);
    
    display: grid;
    place-items: center;
    padding: 4rem 0;
    // background-color: white;
    .lms-wrapper{
        .lg-title{
            font-weight: 600;
            font-size: 1.7rem;
            text-align: center;
            margin: rem 0;
        }
        .login-container{
            padding: 4rem 2.5rem;
            min-width: 38rem;
           
            label{
                font-size: 1.2rem;
            }

            .password-input{
                position: relative;
                
                .password-closed-img{
                    display: none;
                }
            }
            input{
                background-color: transparent;
                padding: 1rem .4rem;
                border: 1px solid black;
                font-weight: 400;
                font-size: 1.3rem;
                width: 100%;
                color: black;
                margin-bottom: 2rem;
                
                &:focus{
                    border: 1px solid rgb(0, 0, 0);
                }
            }


            .login-error{
                margin: 2rem 0;
                margin-bottom: 3rem;
                background-color: black;
                text-align: center;
                width: 100%;
                padding: 1.5rem 0;
                span{
                    padding: 2rem 0;
                    font-size: 1.3rem;
                    width: 100%;
                    color: red;
                    font-weight: 600;
                }
            }


            .login-button-wrapper{
                margin-bottom: 1rem;
                display: flex;
                button{
                    all: unset;
                    padding: .8rem 2.5rem;
                    font-size: 1.3rem;
                    // font-weight: bold;
                    text-transform: capitalize;
                    background-color: black;
                    cursor: pointer;
                    color: white;
                    width:100%;
                    margin-bottom: 1rem;
                    text-align: center;
                    &:hover{
                        opacity: .8;
                    }
                }
            }

            p{
                font-size: 1.2rem;
                font-weight: 500;
                color: black;
                // opacity: .8;

                a{
                    opacity: 1;
                    color: black;
                    text-decoration: underline;
                    font-size: 1.2rem;
                }
            }
        }
    }
}

</style>
