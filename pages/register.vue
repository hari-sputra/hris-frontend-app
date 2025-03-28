<template>
    <section class="py-[50px] flex flex-col items-center justify-center px-4">
        <img src="/svgs/logo-type.svg" alt="">
        <div class="text-[32px] font-semibold text-dark mt-[70px]">
            Sign Up
        </div>
        <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
            Manage your employees to achieve <br> a bigger goals for your company
        </p>
        <form class="w-full card" @submit.prevent="userRegister">
            <div class="form-group">
                <label class="text-grey">Name</label>
                <input type="text" class="input-field" v-model="register.name">
            </div>
            <div class="form-group">
                <label class="text-grey">Email Address</label>
                <input type="email" class="input-field" v-model="register.email">
            </div>
            <div class="form-group">
                <label class="text-grey">Password</label>
                <input type="password" class="input-field" v-model="register.password">
            </div>
            <button type="submit" class="w-full btn btn-primary mt-[14px]">
                Continue
            </button>
        </form>
        <p class="mt-3">Already have an account? <nuxt-link :to="{ name: 'login' }"
                class="font-semibold text-primary hover:text-blue-600">Sign In</nuxt-link>
        </p>
    </section>
</template>

<script>
export default {
    auth: 'guest',
    data() {
        return {
            register: {
                name: '',
                email: '',
                password: ''
            }
        }
    },
    methods: {
        async userRegister() {
            try {
                let response = await this.$axios.post('/register', this.register);
                try {
                    let login = await this.$auth.loginWith('local', {
                        data: {
                            name: this.register.name,
                            email: this.register.email,
                            password: this.register.password,
                        },
                    });
                    console.log(login)
                    this.$router.push('/')
                } catch (err) {
                    console.log(err)
                }
                console.log(response);
            } catch (err) {
                console.log(err)
            }

        }
    }
}
</script>