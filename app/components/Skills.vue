<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface SkillItem { name: string; level: number }
interface SkillCategory { title: string; icon: string; skills: SkillItem[] }

const skillCategories = ref<SkillCategory[]>([
    { title: 'Frontend Development', icon: '💻', skills: [ { name: 'Vue.js / Nuxt 3', level: 90 }, { name: 'Tailwind CSS', level: 85 }, { name: 'JavaScript / TypeScript', level: 80 } ] },
    { title: 'Backend Development', icon: '⚙️', skills: [ { name: 'Node.js / Express.js', level: 80 }, { name: 'PHP / Laravel', level: 75 }, { name: 'LINE API / LIFF', level: 85 } ] },
    { title: 'Database & Tools', icon: '🗄️', skills: [ { name: 'MySQL', level: 85 }, { name: 'Prisma ORM', level: 80 }, { name: 'Git / Version Control', level: 75 } ] }
])

const showBars = ref(false)

onMounted(() => {
    const observer = new IntersectionObserver((entries) => {
        if (entries[ 0 ].isIntersecting) {
            showBars.value = true // สั่งให้หลอดพลังทำงาน
            observer.disconnect()
        }
    }, { threshold: 0.2 })

    // แก้ชื่อ ID ให้ตรงกับแท็ก <section id="Skills"> ด้านล่าง
    const section = document.getElementById('Skills')
    if (section) observer.observe(section)
})
</script>

<template>
    <section id="Skills" class="py-20 bg-slate-900 overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

            <div
                :class="[ 'text-center mb-16 transition-all duration-1000 ease-out', showBars ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12' ]">
                <h2 class="text-3xl md:text-4xl font-extrabold text-white mb-4">ทักษะและความเชี่ยวชาญ</h2>
                <div class="w-20 h-1 bg-blue-500 mx-auto rounded-full mb-4"></div>
                <p class="text-slate-400 max-w-2xl mx-auto text-lg">
                    เทคโนโลยีและเครื่องมือที่ผมใช้งานเป็นประจำในการพัฒนาเว็บไซต์และแอปพลิเคชัน
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div v-for="(category, index) in skillCategories" :key="index"
                    :class="[ 'bg-slate-800 rounded-2xl shadow-lg border border-slate-700 p-8 hover:-translate-y-2 hover:border-blue-500/50 transition-all duration-300', showBars ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12' ]"
                    :style="{ transitionDuration: '700ms', transitionDelay: `${index * 200}ms` }">

                    <div class="flex items-center gap-4 mb-8">
                        <span class="text-3xl animate-bounce">{{ category.icon }}</span>
                        <h3 class="text-xl font-bold text-white">{{ category.title }}</h3>
                    </div>

                    <div class="space-y-6">
                        <div v-for="(skill, skillIndex) in category.skills" :key="skillIndex">
                            <div class="flex justify-between mb-2">
                                <span class="text-sm font-semibold text-slate-200">{{ skill.name }}</span>
                                <span class="text-sm font-bold text-blue-400">{{ skill.level }}%</span>
                            </div>
                            <div class="w-full bg-slate-700 rounded-full h-2.5 overflow-hidden">
                                <div class="bg-gradient-to-r from-blue-500 to-cyan-400 h-2.5 rounded-full transition-all duration-1000 ease-out"
                                    :style="{ width: showBars ? `${skill.level}%` : '0%', transitionDelay: `${(index * 200) + (skillIndex * 150)}ms` }">
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </section>
</template>