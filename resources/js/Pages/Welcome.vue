<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

function handleImageError() {
    document.getElementById('screenshot-container')?.classList.add('!hidden');
    document.getElementById('docs-card')?.classList.add('!row-span-1');
    document.getElementById('docs-card-content')?.classList.add('!flex-row');
    document.getElementById('background')?.classList.add('!hidden');
}
</script>
<!--LANDING PAGE-->
<template>
    <Head title="Welcome to Hivye" />
    <div class="bg-gray-50 text-gray-800 dark:bg-gray-900 dark:text-gray-300 min-h-screen">
    
        <!-- Header -->
        <header class="sticky top-0 z-50 bg-white dark:bg-gray-900 shadow-md">
            <div class="max-w-6xl mx-auto flex justify-between items-center py-4 px-6">
                
                <!-- Logo -->
                <div class="text-xl font-bold text-[#FF2D20] dark:text-white">
                    Hivye
                </div>

                <!-- Navigation -->
                <nav v-if="canLogin" class="flex space-x-4">
                    <Link
                        v-if="$page.props.auth.user"
                        :href="route('dashboard')"
                        class="px-4 py-2 rounded-md text-gray-800 dark:text-white transition hover:text-[#FF2D20] dark:hover:text-[#FF2D20]"
                    >
                        Dashboard
                    </Link>

                    <template v-else>
                        <Link
                            :href="route('login')"
                            class="px-4 py-2 rounded-md text-gray-800 dark:text-white transition hover:text-[#FF2D20] dark:hover:text-[#FF2D20]"
                        >
                            Log in
                        </Link>

                        <Link
                            v-if="canRegister"
                            :href="route('register')"
                            class="px-4 py-2 rounded-md bg-[#FF2D20] text-white transition hover:bg-[#d9261b]"
                        >
                            Register
                        </Link>
                    </template>
                </nav>
            </div>
        </header>

        <!-- Welcome to Hivye Section -->
        <main class="mt-16 text-center">
            <h1 class="text-4xl font-extrabold text-gray-900 dark:text-white">
                Welcome to <span class="text-[#FF2D20]">Hivye</span>
            </h1>
            <p class="mt-4 text-lg text-gray-600 dark:text-gray-400">
                Add description here hoho. long long long long
            </p>

            <div class="mt-6 flex justify-center space-x-4">
                <Link 
                    v-if="!$page.props.auth.user" 
                    :href="route('register')" 
                    class="px-6 py-3 rounded-lg bg-[#FF2D20] text-white text-lg font-medium transition hover:bg-[#d9261b]"
                >
                    Get Started
                </Link>
                <Link 
                    :href="route('dashboard')" 
                    disabled
                    class="px-6 py-3 rounded-lg border border-gray-400 dark:border-gray-600 text-lg font-medium transition opacity-50 cursor-not-allowed"
                >
                    Learn More
                </Link>
            </div>
        </main>

        <!-- Footer -->
        <footer class="mt-16 py-6 text-center text-sm text-gray-500 dark:text-gray-400">
            &copy; 2025 Hivye. All rights reserved.
        </footer>

    </div>
</template>
