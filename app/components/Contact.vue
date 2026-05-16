<script setup lang="ts">
import { ref, onMounted } from 'vue'

// ตัวแปรสำหรับเก็บค่าจากฟอร์ม
const formData = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
})

// ตัวแปรควบคุมแอนิเมชัน
const isVisible = ref(false)

// ฟังก์ชันเมื่อผู้ใช้กดส่งฟอร์ม
const handleSubmit = () => {
    alert(`ขอบคุณครับคุณ ${formData.value.name} ระบบได้รับข้อความของคุณแล้ว! (นี่คือฟังก์ชันจำลอง)`)
    // เคลียร์ค่าในฟอร์มหลังจากส่งเสร็จ
    formData.value = { name: '', email: '', subject: '', message: '' }
}

onMounted(() => {
    // ใช้ IntersectionObserver ตรวจจับการเลื่อนหน้าจอ
    const observer = new IntersectionObserver((entries) => {
        if (entries[ 0 ].isIntersecting) {
            isVisible.value = true
            observer.disconnect() // ทำงานครั้งเดียวแล้วเลิกจับ
        }
    }, { threshold: 0.1 })

    const section = document.getElementById('Contact')
    if (section) observer.observe(section)
})
</script>

<template>
    <section id="Contact" class="py-20 bg-slate-950 overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

            <div
                :class="[ 'text-center mb-16 transition-all duration-1000 ease-out', isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12' ]">
                <h2 class="text-3xl md:text-4xl font-extrabold text-white mb-4">ติดต่อฉัน</h2>
                <div class="w-20 h-1 bg-blue-500 mx-auto rounded-full mb-4"></div>
                <p class="text-slate-400 max-w-2xl mx-auto text-lg">
                    มีโปรเจ็กต์ที่อยากให้ช่วยพัฒนา หรือต้องการสอบถามข้อมูลเพิ่มเติม ยินดีต้อนรับทุกการติดต่อครับ
                </p>
            </div>

            <div class="flex justify-center items-center">

                <div
                    :class="[ 'lg:col-span-2 space-y-6 transition-all duration-1000 ease-out delay-200', isVisible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-12' ]">
                    <div class="bg-slate-900 border border-slate-800 rounded-2xl p-8 space-y-6">
                        <h3 class="text-xl font-bold text-white mb-4">ช่องทางการติดต่อ</h3>

                        <div class="flex items-center gap-4 group">
                            <div
                                class="w-12 h-12 bg-blue-900/40 border border-blue-800 text-blue-400 rounded-xl flex items-center justify-center group-hover:bg-blue-600 group-hover:text-white transition-colors duration-300">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z">
                                    </path>
                                </svg>
                            </div>
                            <div>
                                <p class="text-xs text-slate-500 font-medium">อีเมลของผม</p>
                                <a href="mailto:natthpatphummek@gmail.com"
                                    class="text-sm font-semibold text-slate-200 hover:text-blue-400 transition-colors">natthpatphummek@gmail.com</a>
                            </div>
                        </div>

                        <div class="flex items-center gap-4">
                            <div
                                class="w-12 h-12 bg-emerald-900/40 border border-emerald-800 text-emerald-400 rounded-xl flex items-center justify-center">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z">
                                    </path>
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                                </svg>
                            </div>
                            <div>
                                <p class="text-xs text-slate-500 font-medium">พื้นที่รับงาน</p>
                                <p class="text-sm font-semibold text-slate-200">กรุงเทพฯ / Work from Home (Remote)</p>
                            </div>
                        </div>

                        <div class="pt-6 border-t border-slate-800">
                            <p class="text-sm text-slate-400 mb-4">ติดตามผลงานทาง:</p>
                            <div class="flex gap-4">
                                <a href="https://github.com/Fesnatthpat" target="_blank"
                                    class="w-10 h-10 bg-slate-800 hover:bg-slate-700 text-slate-400 hover:text-white rounded-lg flex items-center justify-center transition-all duration-300 hover:-translate-y-1 hover:shadow-lg">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                                        <path fill-rule="evenodd"
                                            d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
                                            clip-rule="evenodd"></path>
                                    </svg>
                                </a>

                                <!-- <a href="https://facebook.com/yourusername" target="_blank"
                                    class="w-10 h-10 bg-slate-800 hover:bg-blue-600 text-slate-400 hover:text-white rounded-lg flex items-center justify-center transition-all duration-300 hover:-translate-y-1 hover:shadow-lg">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                                        <path fill-rule="evenodd"
                                            d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z"
                                            clip-rule="evenodd"></path>
                                    </svg>
                                </a> -->
                            </div>
                        </div>
                    </div>
                </div>

                <!-- <div
                    :class="[ 'lg:col-span-3 transition-all duration-1000 ease-out delay-400', isVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-12' ]">
                    <form @submit.prevent="handleSubmit"
                        class="bg-slate-900 border border-slate-800 rounded-2xl p-8 space-y-6 shadow-xl">

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
                            <div>
                                <label class="block text-sm font-medium text-slate-300 mb-2">ชื่อของคุณ</label>
                                <input v-model="formData.name" type="text" required
                                    class="w-full bg-slate-800 border border-slate-700 rounded-xl px-4 py-3 text-white placeholder-slate-500 focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all text-sm"
                                    placeholder="สมชาย ใจดี" />
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-slate-300 mb-2">อีเมลติดต่อกลับ</label>
                                <input v-model="formData.email" type="email" required
                                    class="w-full bg-slate-800 border border-slate-700 rounded-xl px-4 py-3 text-white placeholder-slate-500 focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all text-sm"
                                    placeholder="somchai@email.com" />
                            </div>
                        </div>

                        <div>
                            <label class="block text-sm font-medium text-slate-300 mb-2">เรื่องที่ต้องการติดต่อ</label>
                            <input v-model="formData.subject" type="text" required
                                class="w-full bg-slate-800 border border-slate-700 rounded-xl px-4 py-3 text-white placeholder-slate-500 focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all text-sm"
                                placeholder="สนใจจ้างทำเว็บไซต์ POS / สอบถามราคา" />
                        </div>

                        <div>
                            <label class="block text-sm font-medium text-slate-300 mb-2">รายละเอียดข้อความ</label>
                            <textarea v-model="formData.message" rows="5" required
                                class="w-full bg-slate-800 border border-slate-700 rounded-xl px-4 py-3 text-white placeholder-slate-500 focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all text-sm resize-none"
                                placeholder="พิมพ์ข้อความของคุณที่นี่..."></textarea>
                        </div>

                        <button type="submit"
                            class="w-full sm:w-auto px-8 py-3 bg-blue-600 hover:bg-blue-500 text-white font-semibold rounded-xl shadow-md hover:shadow-[0_0_20px_rgba(37,99,235,0.4)] transition-all duration-300 transform hover:-translate-y-0.5">
                            ส่งข้อความติดต่อ
                        </button>

                    </form>
                </div> -->

            </div>

        </div>
    </section>
</template>