<template>
    <section class="text-white mt-20" id="testimonials" data-aos="zoom-in">
        <h2 class="text-4xl font-bold text-white text-left mb-4 px-4 xl:pl-16">Testimonials</h2>
        <div class="px-4 xl:px-16">
            <Carousel v-bind="settings" :breakpoints="breakpoints">
                <Slide v-for="testimonial in testimonials" :key="testimonial.id">
                    <div class="carousel__item p-4">
                        <div
                            class="w-full mx-auto bg-[#111a3e] shadow-lg border border-[#1f1641] p-5 text-white font-light mb-6">
                            <div class="w-full flex mb-4 items-center">
                                <div class="overflow-hidden rounded-full w-10 h-10 bg-gray-50 border border-gray-200">
                                    <img :src="`/hansfolio/assets/${testimonial.image}`" alt="testimonial image"
                                        loading="lazy">
                                </div>
                                <h6 class="ml-4 font-bold text-sm uppercase text-white">{{ testimonial.fullName }}</h6>
                            </div>
                            <div class="w-full">
                                <p class="text-sm leading-tight">
                                    <span class="text-lg leading-none italic font-bold text-white mr-1">"</span>
                                    {{ testimonial.comment }}
                                    <span class="text-lg leading-none italic font-bold text-white mr-1">"</span>
                                </p>
                            </div>
                        </div>
                    </div>
                </Slide>
                <template #addons>
                    <Navigation />
                </template>
            </Carousel>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import { Carousel, Navigation, Slide } from 'vue3-carousel';
import 'vue3-carousel/dist/carousel.css';

const settings = ref({
    itemsToShow: 1,
    snapAlign: 'center',
});

const breakpoints = ref({
    700: {
        itemsToShow: 2.5,
        snapAlign: 'center',
    },
    1024: {
        itemsToShow: 3,
        snapAlign: 'start'
    }
});

const testimonials = ref([
    {
        id: 1,
        fullName: 'client 1',
        image: 'image.png',
        comment: 'Lorem update ipsum dolor sit amet, consectetur adipisicing elit. Suscipit repellat esse repellendus provident placeat quas quae dolor, aperiam labore officia.',
    },
    {
        id: 2,
        fullName: 'client 2',
        image: 'image.png',
        comment: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Suscipit repellat esse repellendus provident placeat quas quae dolor, aperiam labore officia.',
    },
    {
        id: 3,
        fullName: 'client 3',
        image: 'image.png',
        comment: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Suscipit repellat esse repellendus provident placeat quas quae dolor, aperiam labore officia.',
    },
    {
        id: 4,
        fullName: 'client 4',
        image: 'image.png',
        comment: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Suscipit repellat esse repellendus provident placeat quas quae dolor, aperiam labore officia.',
    },
    {
        id: 4,
        fullName: 'client 4',
        image: 'image.png',
        comment: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Suscipit repellat esse repellendus provident placeat quas quae dolor, aperiam labore officia.',
    },
]);

</script>

<style>
.carousel__prev,
.carousel__next {
    color: white !important;
}
</style>