<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isLoaded = ref(false)

onMounted(() => {
    setTimeout(() => {
        isLoaded.value = true
    }, 200)
})
</script>

<template>
    <main class="min-h-screen bg-slate-900 flex items-center pt-20 pb-12 overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full">
            <div class="flex flex-col-reverse md:flex-row items-center justify-between gap-12">

                <div class="w-full md:w-1/2 flex flex-col justify-center text-center md:text-left">
                    <p :class="['text-blue-400 font-semibold tracking-wide text-sm md:text-base uppercase mb-3 transition-all duration-700 ease-out delay-100', isLoaded ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8']">
                        สวัสดีครับ 👋 ยินดีต้อนรับสู่พอร์ตโฟลิโอของผม
                    </p>

                    <h1 :class="['text-4xl md:text-6xl font-extrabold text-white leading-tight mb-4 transition-all duration-700 ease-out delay-300', isLoaded ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8']">
                        ผมคือ <br class="hidden md:block" />
                        <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-cyan-400">
                            Web Developer
                        </span>
                    </h1>

                    <p :class="['text-slate-400 text-base md:text-lg mb-8 max-w-lg mx-auto md:mx-0 leading-relaxed transition-all duration-700 ease-out delay-500', isLoaded ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8']">
                        ผมหลงใหลในการเขียนโค้ดและสร้างสรรค์เว็บไซต์ที่สวยงาม ใช้งานง่าย และมีประสิทธิภาพสูง
                        เชี่ยวชาญในการพัฒนาทั้งระบบ Frontend และ Backend พร้อมเรียนรู้เทคโนโลยีใหม่ๆ อยู่เสมอ
                    </p>

                    <div :class="['flex flex-col sm:flex-row items-center gap-4 justify-center md:justify-start transition-all duration-700 ease-out delay-700', isLoaded ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8']">
                        <a href="#portfolio" class="w-full sm:w-auto px-8 py-3 bg-blue-600 hover:bg-blue-500 text-white font-medium rounded-lg shadow-md transition-all duration-300 transform hover:-translate-y-1 text-center">
                            ดูผลงานของผม
                        </a>
                        <a href="#contact" class="w-full sm:w-auto px-8 py-3 bg-slate-800 hover:bg-slate-700 text-slate-200 font-medium rounded-lg border border-slate-700 shadow-sm transition-all duration-300 text-center">
                            ติดต่อพูดคุย
                        </a>
                    </div>

                    <div :class="['mt-10 transition-all duration-700 ease-out delay-1000', isLoaded ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8']">
                        <p class="text-sm text-slate-500 mb-3 font-medium">เทคโนโลยีที่ผมใช้งาน:</p>
                        <div class="flex flex-wrap gap-3 justify-center md:justify-start">
                            <span class="px-3 py-1 bg-blue-900/50 border border-blue-800 text-blue-300 rounded-full text-xs font-semibold hover:scale-110 transition-transform cursor-pointer">Vue.js</span>
                            <span class="px-3 py-1 bg-green-900/50 border border-green-800 text-green-300 rounded-full text-xs font-semibold hover:scale-110 transition-transform cursor-pointer">Nuxt.js</span>
                            <span class="px-3 py-1 bg-cyan-900/50 border border-cyan-800 text-cyan-300 rounded-full text-xs font-semibold hover:scale-110 transition-transform cursor-pointer">Tailwind CSS</span>
                            <span class="px-3 py-1 bg-yellow-900/50 border border-yellow-800 text-yellow-300 rounded-full text-xs font-semibold hover:scale-110 transition-transform cursor-pointer">JavaScript / TS</span>
                        </div>
                    </div>
                </div>

                <div :class="['w-full md:w-1/2 flex justify-center md:justify-end transition-all duration-1000 ease-out delay-300', isLoaded ? 'opacity-100 scale-100' : 'opacity-0 scale-90']">
                    <div class="relative w-64 h-64 md:w-96 md:h-96">
                        <div class="absolute inset-0 bg-gradient-to-tr from-blue-500 to-cyan-500 rounded-full blur-3xl opacity-30 animate-pulse"></div>

                        <div class="relative w-full h-full rounded-full border-4 border-slate-800 shadow-2xl overflow-hidden bg-slate-800 group">
                            <img src="/images/profile.jpg" alt="My Profile Picture" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
                        </div>

                        <div class="absolute bottom-4 -left-8 md:bottom-10 md:-left-12 bg-slate-800 p-3 rounded-lg shadow-xl border border-slate-700 flex items-center gap-3 animate-bounce">
                            <div class="w-10 h-10 bg-green-900/50 rounded-full flex items-center justify-center text-green-400">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path>
                                </svg>
                            </div>
                            <div>
                                <p class="text-xs text-slate-400 font-medium">ประสบการณ์</p>
                                <p class="text-sm font-bold text-white">Web Dev</p>
                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </main>
</template>