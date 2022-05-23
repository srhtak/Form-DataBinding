<script>
export default {
    data() {
        return {
            form_firstName: '',
            form_lastName: '',
            form_email: '',
            form_password: '',
            form_userType: null,
            form_rememberMe: false,
            form_skills: [],
            temp_skill: '',
            userType: [
                { name: 'User', id: 1 },
                { name: 'Admin', id: 2 },
                { name: 'Test', id: 3 },
            ],
        };
    },
    methods: {
        addSkills() {
            if (this.temp_skill) {
                if (!this.form_skills.includes(this.temp_skill)) {
                    this.form_skills.push(this.temp_skill);
                    this.temp_skill = '';
                }
            }
        },
        deleteSkills(skill) {
            if (this.form_skills.includes(skill)) {
                this.form_skills = this.form_skills.filter(item => item != skill);
            }
        },
    },
};
</script>

<template>
    <div class="grid min-h-screen place-items-center">
        <div class="w-11/12 p-12 bg-white sm:w-8/12 md:w-1/2 lg:w-5/12">
            <h1 class="text-xl font-semibold">
                Hello there 👋,
                <span class="font-normal">please fill in your information to continue</span>
            </h1>
            <div class="mt-6">
                <div class="flex justify-between gap-3">
                    <span class="w-1/2">
                        <label for="firstname" class="block text-xs font-semibold text-gray-600 uppercase"
                            >Firstname</label
                        >
                        <input
                            v-model="form_firstName"
                            id="firstname"
                            type="text"
                            name="firstname"
                            placeholder="John"
                            autocomplete="given-name"
                            class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                        />
                    </span>
                    <span class="w-1/2">
                        <label for="lastname" class="block text-xs font-semibold text-gray-600 uppercase"
                            >Lastname</label
                        >
                        <input
                            v-model="form_lastName"
                            id="lastname"
                            type="text"
                            name="lastname"
                            placeholder="Doe"
                            autocomplete="family-name"
                            class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                        />
                    </span>
                </div>
                <label for="email" class="block mt-2 text-xs font-semibold text-gray-600 uppercase">E-mail</label>
                <input
                    v-model="form_email"
                    id="email"
                    type="email"
                    name="email"
                    placeholder="john.doe@company.com"
                    autocomplete="email"
                    class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                />
                <label for="password" class="block mt-2 text-xs font-semibold text-gray-600 uppercase">Password</label>
                <input
                    v-model="form_password"
                    id="password"
                    type="password"
                    name="password"
                    placeholder="********"
                    autocomplete="new-password"
                    class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                />
                <label for="skills" class="block mt-2 text-xs font-semibold text-gray-600 uppercase">SKILLS</label>
                <input
                    @keydown.enter="addSkills"
                    v-model="temp_skill"
                    id="skilss"
                    type="text"
                    name="skilss"
                    class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                />
                <strong
                    v-for="skill in form_skills"
                    :key="skill"
                    class="m-2 inline-flex items-center border border-blue-500 text-blue-500 border-current uppercase px-5 py-1.5 rounded-full text-[10px] tracking-wide"
                >
                    {{ skill }}

                    <button
                        @click="deleteSkills(skill)"
                        class="p-1 bg-red-100 hover:opacity-75 transition-opacity rounded-full ml-2.5 -mr-2.5 focus:outline-none focus:ring"
                        type="button"
                    >
                        <span class="sr-only"> Close </span>

                        <svg class="w-3 h-3" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="red">
                            <path
                                fill-rule="evenodd"
                                d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                                clip-rule="evenodd"
                            />
                        </svg>
                    </button>
                </strong>
                <h1 class="font-semibold text-gray-600 text-xs mt-2">USER TYPE</h1>
                <div class="flex justify-evenly p-2">
                    <div class="flex-row" v-for="user in userType" :key="user.id">
                        <label class="mr-2 font-semibold" :for="user.id">{{ user.name }}</label>
                        <input class="bg-red-500" v-model="form_userType" type="radio" :id="user.id" :value="user.id" />
                    </div>
                </div>
                <div class="flex justify-items-start">
                    <label name="remember" for="remember" class="text-right font-semibold mr-2">Remember Me:</label>
                    <input
                        v-model="form_rememberMe"
                        type="checkbox"
                        class="text-center mt-1.5"
                        id="remember"
                        name="remember"
                    />
                </div>
                <button
                    class="w-full py-3 mt-6 font-medium tracking-widest text-white uppercase bg-black shadow-lg focus:outline-none hover:bg-gray-900 hover:shadow-none"
                >
                    Sign up
                </button>
                <p class="flex justify-between inline-block mt-4 text-xs text-gray-500 cursor-pointer hover:text-black">
                    Already registered?
                </p>
            </div>
        </div>
    </div>
</template>

<style></style>
