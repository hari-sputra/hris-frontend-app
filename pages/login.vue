<template>
    <div>
        <section class="py-[50px] flex flex-col items-center justify-center px-4">
            <img src="/svgs/logo-type.svg" alt="">
            <div class="text-[32px] font-semibold text-dark mt-[70px]">
                Sign In
            </div>
            <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
                Manage your employees to achieve <br> a bigger goals for your company
            </p>
            <form class="w-full card" @submit.prevent="userLogin">
                <div class="form-group">
                    <label class="text-grey">Email Address</label>
                    <input type="email" class="input-field" v-model="login.email">
                </div>
                <div class="form-group">
                    <label class="text-grey">Password</label>
                    <input type="password" class="input-field" v-model="login.password">
                </div>
                <button type="submit" class="w-full btn btn-primary mt-[14px]">
                    Sign In
                </button>
            </form>
            <p class="mt-3">Don't have an account yet? <nuxt-link :to="{ name: 'register' }"
                    class="font-semibold text-primary hover:text-blue-600">Sign Up</nuxt-link>
            </p>

        </section>
    </div>
</template>
<script>
export default {
    auth: 'guest',
    data() {
        return {
            login: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
        async userLogin() {
            try {
                let response = await this.$auth.loginWith('local', { data: this.login })
                console.log(response)
                this.$router.push('/')
            } catch (err) {
                console.log(err)
            }
        }
    }
}
</script>