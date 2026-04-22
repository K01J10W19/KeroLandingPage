<script setup>
    import { motion } from 'motion-v'
    import { Plus } from 'lucide-vue-next'

    import Testimonial01 from '@/assets/images/Customer_testimonial.webp'
    import Testimonial02 from '@/assets/images/Customer_testimonial_02.webp'
    import Testimonial03 from '@/assets/images/Customer_testimonial_03.webp'
    import Testimonial04 from '@/assets/images/Customer_testimonial_04.webp'


    const testimonials = [
        {
            type: 'landscape',
            name: 'James Gawley',
            role: 'CEO NeoRick',
            text: '"This tool transformed how we do research. We can scan sources, generate summaries, and deliver insights in a fraction of the time."',
            image: Testimonial01,
            span: 'md:col-start-1 md:col-end-7 md:row-start-1 md:row-end-3 z-0'
        },
        {
            type: 'logo',
            icon: 'https://api.iconify.design/simple-icons:paycare.svg',
            span: 'md:flex md:col-start-7 md:col-end-10 md:row-start-1 md:row-end-3 z-10 md:-ml-8'
        },
        {
            type: 'portrait',
            name: 'PayCare',
            brand: 'PayCare',
            image: Testimonial02,
            span: 'md:col-start-9 md:col-end-13 md:row-start-1 md:row-end-3 z-20 md:-ml-12'
        },
        {
            type: 'portrait',
            name: 'Team Member',
            brand: 'Colfare',
            image: Testimonial03,
            span: 'md:col-start-1 md:col-end-5 md:row-start-3 md:row-end-5 z-0'
        },
        {
            type: 'logo',
            icon: 'https://api.iconify.design/simple-icons:analyx.svg',
            span: 'md:flex md:col-start-4 md:col-end-8 md:row-start-3 md:row-end-5 z-10 md:-ml-8'
        },
        {
            type: 'landscape',
            name: 'Sophia Kunz',
            role: 'CTO Analyx',
            text: '"The AI research analyst helps our team scan information quickly, making strategic decisions easier and far more data-driven."',
            image: Testimonial04,
            span: 'md:col-start-7 md:col-end-13 md:row-start-3 md:row-end-5 z-20 md:-ml-12'
        }
    ]
    
    // 1. The Parent (Orchestrator)
    const containerVariants = {
        hidden: { opacity: 0 },
        visible: {
            opacity: 1,
            transition: {
                // Each child will wait 0.4s after the previous one starts
                staggerChildren: 0.3, 
                delayChildren: 0.2
            },
        },
    }

    const cardFade = {
        hidden: { opacity: 0, scale: 0.95, y: 50 },
        visible: { 
            opacity: 1, 
            scale: 1, 
            y: 0,
            transition: { duration: 1.2, ease: [0.16, 1, 0.3, 1] } 
        }
    }

    const fadeUp = {
        hidden: { opacity: 0, y: 40 },
        visible: { 
            opacity: 1, 
            y: 0, 
            transition: { duration: 0.8, ease: [0.22, 1, 0.36, 1] } 
        }
    }
</script>

<template>
    <section class="bg-bg-primary py-[var(--spacing-section-y)] px-8 md:px-16 lg:px-24">
        <div class="max-w-[1920px] mx-auto"> 
            <header class="text-center mb-16 md:mb-24">
                <motion.h2 class="font-heading text-[clamp(1.5rem,5vw,3.5rem)] mb-6 text-text-main"
                    initial="hidden"
                    whileInView="visible"
                    :viewport="{ once: true }"
                    :variants="fadeUp"
                >
                    Hear from customers like you
                </motion.h2>

                <motion.p class="text-text-muted text-[clamp(1rem,2vw,1.75rem)] max-w-3xl mx-auto leading-relaxed"
                    initial="hidden"
                    whileInView="visible"
                    :viewport="{ once: true }"
                    :variants="fadeUp"
                >
                    Discover what brought them to us, what they tried before, and how they work today.
                </motion.p>
            </header>

            <motion.div class="grid grid-cols-1 md:grid-cols-12 gap-4 auto-rows-[320px] md:auto-rows-[160px]"
                        :variants="containerVariants"
                        initial="hidden"
                        whileInView="visible"
                        :viewport="{ once: true, amount: 0.4, margin: '0px 0px -100px 0px'}"
            >
                
                <motion.div 
                    v-for="(item, index) in testimonials" 
                    :key="index"
                    :variants="cardFade"
                    :class="[
                        'relative rounded-[2rem] overflow-hidden group',
                        item.span
                    ]"
                >
                    <template v-if="item.type === 'landscape'">
                        <img :src="item.image" class="absolute inset-0 w-full h-full object-cover opacity-60 mix-blend-luminosity grayscale-[0.5] group-hover:grayscale-0 group-hover:scale-105 transition-all duration-1000" />
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/20 to-transparent" />
                        
                        <div class="relative h-full p-8 flex flex-col justify-between">
                            <div class="flex justify-between items-start opacity-0 translate-y-[-8px] group-hover:opacity-100 group-hover:translate-y-0 transition-all duration-500 ease-out">
                                <div class="text-xs font-medium text-white/80">{{ item.name }} - {{ item.role }}</div>
                            </div>
                            <p class="text-white text-[clamp(0.8rem,1.5vw,1.2rem)] leading-relaxed font-body italic opacity-0 translate-y-4 group-hover:opacity-100 group-hover:translate-y-0 transition-all duration-700 ease-out delay-75">
                                {{ item.text }}
                            </p>
                        </div>
                    </template>

                    <template v-else-if="item.type === 'portrait'">
                        <img :src="item.image" class="absolute inset-0 w-full h-full object-cover group-hover:grayscale-0 group-hover:scale-105 transition-all duration-500" />
                        <div class="absolute bottom-6 left-6 flex items-center gap-2 opacity-0 translate-y-[-8px] group-hover:opacity-100 group-hover:translate-y-0 transition-all duration-500 ease-out">
                            <div class="w-2 h-2 rounded-full bg-white shadow-glow" />
                            <span class="text-white font-bold text-lg italic tracking-tighter">{{ item.brand }}</span>
                        </div>
                    </template>

                    <template v-else-if="item.type === 'logo'">
                        <div class="w-full h-full bg-[#111] flex items-center justify-center p-12 border border-white/5 overflow-hidden">
                            <motion.div 
                                class="w-16 h-16 bg-white/10 rounded-2xl flex items-center justify-center cursor-pointer"
                                
                                :whileHover="{ 
                                    scale: 1.2, 
                                    rotate: 12,
                                    backgroundColor: 'rgba(255, 255, 255, 0.15)'
                                }"
                                :whileTap="{ scale: 0.9 }"
                                
                                :transition="{ 
                                    type: 'spring', 
                                    stiffness: 400, 
                                    damping: 10, 
                                    mass: 1 
                                }"
                            >
                                <div class="w-8 h-8 border-2 border-white/60 rounded-full rotate-45 relative">
                                    <div class="absolute inset-0 m-auto w-1 h-1 bg-white rounded-full" />
                                </div>
                            </motion.div>
                        </div>
                    </template>

                </motion.div>
            </motion.div>
        </div>
    </section>
</template>