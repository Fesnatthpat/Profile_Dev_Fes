<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isMobileMenuOpen = ref(false)
const isLoaded = ref(false)

const toggleMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value
}

// เมื่อโหลดคอมโพเนนต์เสร็จ ให้หน่วงเวลาเล็กน้อยแล้วตั้งค่า isLoaded เป็น true
onMounted(() => {
    setTimeout(() => {
        isLoaded.value = true
    }, 100)
})
</script>

<template>
    <nav :class="['bg-slate-900 border-b border-slate-800 fixed w-full top-0 z-50 transition-all duration-700 ease-out', isLoaded ? 'translate-y-0 opacity-100' : '-translate-y-full opacity-0']">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">

                <div class="flex-shrink-0 flex items-center cursor-pointer">
                    <span class="text-xl font-bold text-white tracking-wider hover:scale-105 transition-transform">
                        DEV<span class="text-blue-500">PORTFOLIO</span>
                    </span>
                </div>

                <div class="hidden md:flex space-x-8">
                    <NuxtLink to="/" class="text-slate-300 hover:text-blue-400 px-3 py-2 text-sm font-medium transition-colors">หน้าแรก</NuxtLink>
                    <NuxtLink to="#Portfolio" class="text-slate-300 hover:text-blue-400 px-3 py-2 text-sm font-medium transition-colors">ผลงาน</NuxtLink>
                    <NuxtLink to="#Skills" class="text-slate-300 hover:text-blue-400 px-3 py-2 text-sm font-medium transition-colors">ทักษะ</NuxtLink>
                    <NuxtLink to="#Contact" class="bg-blue-600 text-white hover:bg-blue-700 px-4 py-2 rounded-md text-sm font-medium transition-all hover:shadow-[0_0_15px_rgba(37,99,235,0.5)]">ติดต่อฉัน</NuxtLink>
                </div>

                <div class="md:hidden flex items-center">
                    <button @click="toggleMenu" class="text-slate-300 hover:text-white focus:outline-none">
                        <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path v-if="!isMobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>

            </div>
        </div>

        <div v-show="isMobileMenuOpen" class="md:hidden bg-slate-900 border-t border-slate-800 shadow-lg absolute w-full">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <NuxtLink to="/" class="block text-slate-300 hover:text-blue-400 hover:bg-slate-800 px-3 py-2 rounded-md text-base font-medium">หน้าแรก</NuxtLink>
                <NuxtLink to="#Portfolio" class="block text-slate-300 hover:text-blue-400 hover:bg-slate-800 px-3 py-2 rounded-md text-base font-medium">ผลงาน</NuxtLink>
                <NuxtLink to="#Skills" class="block text-slate-300 hover:text-blue-400 hover:bg-slate-800 px-3 py-2 rounded-md text-base font-medium">ทักษะ</NuxtLink>
                <NuxtLink to="#Contact" class="block text-center bg-blue-600 text-white hover:bg-blue-700 px-4 py-2 mt-4 rounded-md text-base font-medium">ติดต่อฉัน</NuxtLink>
            </div>
        </div>
    </nav>
    <div class="pt-16"></div>
</template>