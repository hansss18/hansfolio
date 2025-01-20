<template>
    <section class="text-white mt-18" id="about">
        <div class="absolute z-0 top-[93rem] inset-x-0 h-64 flex items-start">
            <div class="h-24 w-64 bg-gradient-to-br from-primary via-secondary blur-2xl to-[#570cac] opacity-20"></div>
        </div>
        <div class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 sm:py-16 xl:px-16 z-1">
            <div data-aos="flip-right">
                <h2 class="text-4xl font-bold text-white text-left mb-8">My Education</h2>
                <div class="space-y-8 py-8">
                    <div v-for="education in educations" :key="education.id"
                        class="flex items-center md:w-[80%] w-full p-5 rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641]">
                        <div class="w-1/4">
                            <img src="https://img.icons8.com/ios-glyphs/60/ffffff/graduation-cap--v1.png"
                                alt="graduation-cap--v1">
                        </div>
                        <div class="w-3/4 pl-4">
                            <h3
                                class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                                {{ education.school }}
                            </h3>
                            <p class="text-white">{{ education.program }}</p>
                            <p class="text-white">{{ education.year }}</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full" data-aos="flip-right">
                <h2 class="text-4xl font-bold text-white md:text-center text-left mb-4">More
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">About</span>
                    Me
                </h2>
                <p class="text-base lg:text-lg mt-8 py-8">
                    {{ t('aboutSection.desc') }}
                </p>
                <div class="flex justify-center items-center pt-8">
                    <div class="grid grid-cols-3 gap-4 max-w-lg">
                        <div v-for="stat in stats" :key="stat.id"
                            class="text-center rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641] p-3">
                            <h3 class="text-white font-bold text-xl sm:text-2xl lg:text-3xl">{{ stat.value }}</h3>
                            <p class="text-sm sm:text-base text-gray-300">{{ stat.label }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import { useI18n } from 'vue-i18n';

const { t } = useI18n();

const data = ref(null);
const loading = ref(true);
const error = ref(null);

const educations = ref([
    {
        id: 1,
        school: 'Politeknik LP3I',
        program: 'D3 - Management Informatics',
        year: '2023',
    },
]);

const stats = ref([
    {
        id: 1,
        value: '+5',
        label: 'Happy Client',
    },
    {
        id: 2,
        value: '+25',
        label: 'Projects',
    },
    {
        id: 3,
        value: '+2',
        label: 'Years Experience',
    }
]);
</script>