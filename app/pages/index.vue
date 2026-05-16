<script setup lang="ts">
// หน้าหลักของเว็บไซต์พอร์ตโฟลิโอ
// เราใช้ <script setup lang="ts"> ตามมาตรฐานของ Vue 3 Composition API
// ไม่จำเป็นต้อง import คอมโพเนนต์ที่นี่ เนื่องจาก Nuxt 3 มีระบบ Auto-import ให้แล้ว
</script>

<template>
    <div class="bg-slate-900 min-h-screen font-sans text-white">

        <!-- <Navbar /> -->

        <Home />

        <Portfolio />

        <Skills />

        <footer class="bg-slate-950 border-t border-slate-800 py-8 text-center">
            <p class="text-slate-400 text-sm">
                &copy; {{ new Date().getFullYear() }} My Portfolio. All rights reserved.
            </p>
        </footer>

    </div>
</template>