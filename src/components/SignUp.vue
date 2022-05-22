<script>
export default {
    data() {
        return {
            form_firstName: "",
            form_lastName: "",
            form_email: "",
            form_password: "",
            form_userType: null,
            form_rememberMe: false,
            userType: [
                { name: "User", id: 1 },
                { name: "Admin", id: 2 },
                { name: "Test", id: 3 },
            ],
        };
    },
};
</script>

<template>
    <div class="grid min-h-screen place-items-center">
        <div class="w-11/12 p-12 bg-white sm:w-8/12 md:w-1/2 lg:w-5/12">
            <h1 class="text-xl font-semibold">
                Hello there 👋,
                <span class="font-normal"
                    >please fill in your information to continue</span
                >
            </h1>
            <form class="mt-6">
                <div class="flex justify-between gap-3">
                    <span class="w-1/2">
                        <label
                            for="firstname"
                            class="block text-xs font-semibold text-gray-600 uppercase"
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
                            required
                        />
                    </span>
                    <span class="w-1/2">
                        <label
                            for="lastname"
                            class="block text-xs font-semibold text-gray-600 uppercase"
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
                            required
                        />
                    </span>
                </div>
                <label
                    for="email"
                    class="block mt-2 text-xs font-semibold text-gray-600 uppercase"
                    >E-mail</label
                >
                <input
                    v-model="form_email"
                    id="email"
                    type="email"
                    name="email"
                    placeholder="john.doe@company.com"
                    autocomplete="email"
                    class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                    required
                />
                <label
                    for="password"
                    class="block mt-2 text-xs font-semibold text-gray-600 uppercase"
                    >Password</label
                >
                <input
                    v-model="form_password"
                    id="password"
                    type="password"
                    name="password"
                    placeholder="********"
                    autocomplete="new-password"
                    class="block w-full p-3 mt-2 text-gray-700 bg-gray-200 appearance-none focus:outline-none focus:bg-gray-300 focus:shadow-inner"
                    required
                />
                <h1 class="font-semibold text-gray-600 text-xs mt-2">
                    USER TYPE
                </h1>
                <div class="flex justify-evenly p-2">
                    <div
                        class="flex-row"
                        v-for="user in userType"
                        :key="user.id"
                    >
                        <label class="mr-2 font-semibold" :for="user.id">{{
                            user.name
                        }}</label>
                        <input
                            class="bg-red-500"
                            v-model="form_userType"
                            type="radio"
                            :id="user.id"
                            :value="user.id"
                        />
                    </div>
                </div>
                <div class="flex justify-items-start">
                    <label
                        name="remember"
                        for="remember"
                        class="text-right font-semibold mr-2"
                        >Remember Me:</label
                    >
                    <input
                        v-model="form_rememberMe"
                        type="checkbox"
                        class="text-center mt-1.5"
                        id="remember"
                        name="remember"
                    />
                </div>
                <button
                    type="submit"
                    class="w-full py-3 mt-6 font-medium tracking-widest text-white uppercase bg-black shadow-lg focus:outline-none hover:bg-gray-900 hover:shadow-none"
                >
                    Sign up
                </button>
                <p
                    class="flex justify-between inline-block mt-4 text-xs text-gray-500 cursor-pointer hover:text-black"
                >
                    Already registered?
                </p>
            </form>
        </div>
    </div>
</template>

<style></style>
