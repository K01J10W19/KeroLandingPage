<script setup>
    import { motion } from 'motion-v'
    import { ArrowRight, Box } from "lucide-vue-next"

    import coverImg from '@/assets/images/Hero_Img.webp'

    const navLinks = ['Product', 'Testimonials', 'Pricing']
    const partners = ['Analyx', 'PayCare', 'NEORICK', 'Colfare']

    const containerVariants = {
        hidden: { opacity: 0 },
        visible: {
            opacity: 1,
            transition: {
                staggerChildren: 0.3, // This now has a target to control
            },
        },
    }

    const itemVariants = {
        hidden: { 
            opacity: 0, 
            y: 16 
        },
        visible: { 
            opacity: 1, 
            y: 0,
            transition: { 
                duration: 1, 
                ease: 'backOut' 
            }
        },
    }
</script>

<template>
    <section class="relative min-h-screen md:min-h-[70vh] w-full overflow-hidden bg-bg-primary text-text-main font-body selection:bg-white selection:text-black">
        
        <div class="absolute inset-0 z-0">
            <img 
                :src="coverImg" 
                class="h-full w-full object-cover opacity-60 mix-blend-luminosity"
                alt="Mountain landscape"
            />
        </div>

        <div class="absolute inset-x-0 bottom-0 h-1/3 z-10 bg-gradient-to-t from-[var(--color-bg-primary)] via-[var(--color-bg-primary)]/80 to-transparent" />

        <nav class="relative z-20 flex items-center justify-between px-8 py-6 md:px-16 lg:px-24">
            <div class="flex items-center gap-2">
                <Box class="w-8 h-8 text-white" /> 
            </div>
            
            <div class="hidden md:flex items-center gap-10 xl:gap-16 text-sm xl:text-lg font-medium tracking-wide">
                <a v-for="link in navLinks" :key="link" href="#" class="hover:opacity-70 transition-opacity">
                    {{ link }}
                </a>
            </div>

            <div class="flex items-center gap-8">
                <a href="#" class="hidden md:block text-sm xl:text-lg font-medium hover:opacity-70 transition-opacity">Contact Us</a>
                <button class="bg-white text-black px-6 py-2 rounded-full text-sm xl:text-lg font-semibold hover:bg-opacity-90 hover:scale-105 cursor-pointer transition-all">
                    Try Free
                </button>
            </div>
        </nav>

        <main class="relative z-10 flex flex-col items-center justify-center text-center px-4 pt-24 pb-16 md:pt-24 xl:pt-32 2xl:pt-48">
        
            <motion.h1 
                :initial="{ opacity: 0, y: 20 }"
                :animate="{ opacity: 1, y: 0 }"
                :transition="{ duration: 0.8, ease: 'easeOut' }"
                class="font-heading text-balance leading-[1.1] tracking-tight max-w-5xl text-[clamp(2.5rem,8vw,5.5rem)] mb-8"
            >
                AI research and analysis for modern teams
            </motion.h1>

            <motion.p 
                :initial="{ opacity: 0 }"
                :animate="{ opacity: 1 }"
                :transition="{ delay: 0.4, duration: 0.8 }"
                class="text-text-muted max-w-2xl mx-auto leading-relaxed mb-12 text-[clamp(1rem,2vw,1.25rem)] px-4"
            >
                Analyze documents, generate reports, and produce executive-ready summaries — all in one tool.
            </motion.p>

            <motion.button 
                :initial="{ scale: 0.9, opacity: 0 }"
                :animate="{ scale: 1, opacity: 1 }"
                :transition="{ delay: 0.6 }"
                class="group flex items-center gap-2 bg-white text-black px-10 py-4 rounded-full font-bold text-lg hover:scale-105 transition-transform cursor-pointer"
            >
                Try for Free
                <ArrowRight class="w-5 h-5 group-hover:translate-x-1 transition-transform" />
            </motion.button>

        </main>

        <div class="relative z-20 mt-auto w-full py-16">
            <motion.div 
                class="max-w-[1920px] mx-auto px-8 grid grid-cols-2 gap-8 justify-items-center md:flex md:flex-wrap md:justify-center md:gap-x-16 xl:gap-x-24 md:gap-y-8 opacity-50 grayscale hover:grayscale-0 transition-all duration-500"
                :variants="containerVariants"
                initial="hidden"
                whileInView="visible"
                :viewport="{ amount: 0.1, once: true }"
            >
                <motion.div 
                    v-for="brand in partners" 
                    :key="brand" class="flex items-center gap-2 font-bold tracking-tighter text-lg md:text-xl italic"
                    :variants="itemVariants"
                >
                    <div class="w-5 h-5 md:w-6 md:h-6 bg-white rounded-sm shrink-0" /> 
                    <span>{{ brand }}</span>
                </motion.div>
            </motion.div>
        </div>

    </section>
</template>