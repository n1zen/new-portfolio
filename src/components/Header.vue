<template>
    <header>
        <div class="container">
            <div class="logo">
                <a href="#home">
                    <span class="logo1">n1zen</span><span class="logo2">.dev</span>
                </a>
            </div>
            <nav>
                <ul>
                    <li><a href="#projects">Projects</a></li>
                    <li><a href="#achievements">Achievements</a></li>
                    <li><a href="#contact">Contact</a></li>
                    <li>
                        <button id="theme-toggle" @click="toggleTheme">
                            <Sun v-if="isDark" :size="24"/>
                            <Moon v-else :size="24"/>
                        </button>
                    </li>
                </ul>
            </nav>
        </div>
    </header>
</template>

<script>
import { Sun, Moon } from 'lucide-vue-next'
export default {
    name: 'Header',
    components: {
        Sun,
        Moon
    },
    data() {
        return {
            isDark: true
        }
    },
    mounted() {
        const saved = localStorage.getItem('theme');
        if (saved === 'light') {
            this.isDark = false;
            document.documentElement.classList.add('light');
        }
    },
    methods: {
        toggleTheme() {
            this.isDark = !this.isDark;
            if (this.isDark) {
                document.documentElement.classList.remove('light');
                localStorage.setItem('theme', 'dark');
            } else {
                document.documentElement.classList.add('light');
                localStorage.setItem('theme', 'light');
            }
        }
    }
}
</script>