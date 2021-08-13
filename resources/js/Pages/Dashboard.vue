<template>
    <Head title="Dashboard" />

<!--    <template >-->
<!--        <h2 class="font-semibold text-xl text-gray-800 leading-tight">-->
<!--            Dashboard-->
<!--        </h2>-->
<!--    </template>-->

<!--    <div class="py-12">-->
<!--        <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">-->
<!--            <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">-->
<!--                <div class="p-6 bg-white border-b border-gray-200">-->
<!--                    You're logged in!-->
<!--                </div>-->
<!--            </div>-->
<!--        </div>-->
<!--    </div>-->

    <BreezeAuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div v-if='!hello'  class="p-6 bg-white border-b border-gray-200">
                        You're logged in!
                    </div>
                    <div v-else class="p-6 bg-white border-b border-gray-200">
                        hello
                    </div>
                </div>
            </div>
        </div>
    </BreezeAuthenticatedLayout>

</template>

<script>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue'
import { Head } from '@inertiajs/inertia-vue3';

export default {
    components: {
        BreezeAuthenticatedLayout,
        Head,
    },

    created() {
        console.log('created');
        Echo.channel('channel').listen('Hello', (event) => {
            console.log(event);
            this.hello = !this.hello;
        })
    },

    mounted() {
        console.log('mounted');
        this.test();
    },

    data() {
        return {
            hello: false
        }
    },

    methods:{
        test() {
            console.log('vue executing');
        }
    }
}
</script>
