<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface Project {
    id: number
    title: string
    description: string
    imageUrl: string
    techStack: string[]
    demoLink: string
    codeLink: string
}

const projects = ref<Project[]>([
    { id: 1, title: 'ระบบ Point of Sale (POS)', description: 'ระบบจัดการหน้าร้านและการขาย รองรับการจัดการสต็อกสินค้าอย่างมีประสิทธิภาพ พร้อมฐานข้อมูลที่รวดเร็วและปลอดภัย', imageUrl: 'https://placehold.co/600x400/1e293b/ffffff?text=POS+System', techStack: [ 'Nuxt 3', 'Prisma', 'MySQL', 'Tailwind' ], demoLink: '#', codeLink: '#' },
    { id: 2, title: 'E-commerce Salepage & Order Management', description: 'หน้าเว็บเซลเพจสำหรับร้านค้าออนไลน์ พร้อมระบบหลังบ้านสำหรับจัดการออเดอร์และการชำระเงินที่ใช้งานง่าย', imageUrl: 'https://placehold.co/600x400/1e293b/ffffff?text=E-commerce+Salepage', techStack: [ 'Laravel', 'Vue.js', 'Tailwind CSS' ], demoLink: '#', codeLink: '#' },
    { id: 3, title: 'LINE LIFF Business Application', description: 'แอปพลิเคชันบน LINE ที่ช่วยให้ธุรกิจสามารถทำการตลาด บริการลูกค้า และส่ง Flex Message โปรโมชันได้อย่างสะดวก', imageUrl: 'https://placehold.co/600x400/1e293b/ffffff?text=LINE+LIFF+App', techStack: [ 'LINE API', 'JavaScript', 'Express.js' ], demoLink: '#', codeLink: '#' }
])

onMounted(() => {
    // สร้าง Observer เพื่อดักจับตอนที่เลื่อนหน้าจอมาเจอคลาส .scroll-anim
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.remove('opacity-0', 'translate-y-12')
                entry.target.classList.add('opacity-100', 'translate-y-0')
                observer.unobserve(entry.target) // ยกเลิกการติดตามเมื่อโชว์แล้ว
            }
        })
    }, { threshold: 0.1 })

    document.querySelectorAll('.scroll-anim').forEach((el) => {
        observer.observe(el)
    })
})
</script>

<template>
    <section id="Portfolio" class="py-20 bg-slate-950 overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

            <div class="text-center mb-16 scroll-anim opacity-0 translate-y-12 transition-all duration-700 ease-out">
                <h2 class="text-3xl md:text-4xl font-extrabold text-white mb-4">ผลงานของผม</h2>
                <div class="w-20 h-1 bg-blue-500 mx-auto rounded-full mb-4"></div>
                <p class="text-slate-400 max-w-2xl mx-auto text-lg">
                    รวมโปรเจ็กต์ที่ผมได้พัฒนาขึ้นเพื่อแก้ปัญหาและสร้างประสบการณ์ที่ดีให้กับผู้ใช้งาน
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div v-for="(project, index) in projects" :key="project.id"
                    class="bg-slate-900 rounded-2xl shadow-lg border border-slate-800 overflow-hidden hover:shadow-[0_0_20px_rgba(59,130,246,0.15)] hover:border-slate-600 transition-all duration-300 group scroll-anim opacity-0 translate-y-12"
                    :style="{ transitionDuration: '700ms', transitionDelay: `${index * 150}ms` }">
                    
                    <div class="relative overflow-hidden h-48">
                        <img :src="project.imageUrl" :alt="project.title"
                            class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-500 opacity-90 group-hover:opacity-100" />
                        <div class="absolute inset-0 bg-gradient-to-t from-slate-900 to-transparent opacity-0 group-hover:opacity-60 transition-opacity duration-300"></div>
                    </div>

                    <div class="p-6">
                        <h3 class="text-xl font-bold text-white mb-2 group-hover:text-blue-400 transition-colors">{{ project.title }}</h3>
                        <p class="text-slate-400 text-sm mb-4 line-clamp-3">
                            {{ project.description }}
                        </p>

                        <div class="flex flex-wrap gap-2 mb-6">
                            <span v-for="(tech, i) in project.techStack" :key="i"
                                class="px-2.5 py-1 bg-slate-800 border border-slate-700 text-slate-300 rounded-md text-xs font-medium">
                                {{ tech }}
                            </span>
                        </div>

                        <div class="flex items-center gap-3 pt-4 border-t border-slate-800">
                            <a :href="project.demoLink" target="_blank"
                                class="flex-1 text-center bg-blue-600 text-white hover:bg-blue-500 px-4 py-2 rounded-lg text-sm font-semibold transition-colors">
                                ดูเว็บไซต์จริง
                            </a>
                            <a :href="project.codeLink" target="_blank"
                                class="flex-1 text-center bg-slate-800 border border-slate-700 text-slate-300 hover:bg-slate-700 px-4 py-2 rounded-lg text-sm font-semibold transition-colors">
                                ดูโค้ด
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>