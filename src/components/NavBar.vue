<template>
    <header class="flex justify-between items-center p-6 bg-opacity-50 relative z-20">
        <div>
            <img src="/assets/icons/logo.png" alt="logo-hans" class="h-20 w-auto">
        </div>
        <!-- Mobile Toggle Button -->
        <div class="md:hidden z-30">
            <button type="button" class="block focus:outline-none" @click="isMenuOpen = !isMenuOpen">
                <span v-if="isMenuOpen" class="text-5xl">
                    <img src="https://img.icons8.com/ios-filled/100/ffffff/delete-sign.png" alt="close" width="50"
                        height="50">
                </span>
                <span v-else class="text-5xl">
                    <img src="https://img.icons8.com/ios-filled/ffffff/menu--v6.png" alt="menu" width="50" height="50">
                </span>
            </button>
        </div>

        <!-- Navbar Link -->
        <nav :class="['fixed inset-0 z-20 flex flex-col items-center justify-center bg-[#111827] md:relative md:bg-transparent md:flex md:justify-between md:flex-row',
            isMenuOpen ? 'block' : 'hidden'
        ]">
            <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0">
                <li v-for="menu in menus" :key="menu.name">
                    <a :href="menu.href"
                        class="block text-white transition hover:text-primary ease-linear text-2xl md:text-lg"
                        @click="scrollToSection(menu.href)">
                        {{ langs(`${menu.name}`) }}
                    </a>
                </li>
                <li>
                    <select v-model="currentLocale" @change="changeLanguage"
                        class="text-white bg-transparent border border-white rounded px-2 py-1">
                        <option v-for="lang in languages" :key="lang.code" :value="lang.code">
                            {{ lang.name }}
                        </option>
                    </select>
                </li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
import { ref, computed } from 'vue';
import { useI18n } from 'vue-i18n';

const langs = (key) => useI18n().t(`navBar.${key}`);

const menus = ref([
    { name: 'service', href: '#services' },
    { name: 'aboutMe', href: '#about' },
    { name: 'skills', href: '#skills' },
    { name: 'projects', href: '#projects' },
    // { name: 'Testimonials', href: '#testimonials' },
    { name: 'contact', href: '#contact' },
]);

const isMenuOpen = ref(false);
const scrollToSection = (href) => {
    isMenuOpen.value = false;
    const section = document.querySelector(href);
    if (section) {
        section.scrollIntoView({ behavior: 'smooth' })
    }
}

const { locale } = useI18n();

const languages = ref([
    { code: 'en', name: 'English' },
    { code: 'id', name: 'Bahasa Indonesia' },
]);

const currentLocale = computed({
    get: () => locale.value,
    set: (newLocale) => {
        locale.value = newLocale;
    },
});

const changeLanguage = () => {
    console.log(`Language changed to: ${locale.value}`);
};
</script>