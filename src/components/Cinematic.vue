<script setup>
    import { motion } from 'motion-v'

    import Cinematic_Img from '@/assets/images/Cinematic_Background_Img.webp'
</script>

<template>
    <section class="bg-bg-primary py-[var(--spacing-section-y)] px-8 flex flex-col items-center justify-center relative overflow-hidden">
        
        <motion.div 
            class="relative w-full max-w-5xl h-[250px] md:h-[400px] mb-12 md:mb-20 flex justify-center"
            :initial="{ opacity: 0, scale: 0.85, y: 60, filter: 'blur(15px)' }"
            :whileInView="{ opacity: 1, scale: 1, y: 0, filter: 'blur(0px)' }"
            :viewport="{ once: true, amount: 0.4 }"
            :transition="{ duration: 1.6, ease: [0.16, 1, 0.3, 1] }"
        >
            <img 
                :src= Cinematic_Img 
                alt="Misty landscape" 
                class="w-full h-full object-cover mix-blend-luminosity vignette-mask"
            />
        </motion.div>

        <motion.p 
            class="font-heading text-white/90 text-center text-[clamp(1.25rem,3vw,2.5rem)] leading-[1.4] max-w-[800px] mx-auto"
            :initial="{ opacity: 0, y: 40, filter: 'blur(10px)' }"
            :whileInView="{ opacity: 1, y: 0, filter: 'blur(0px)' }"
            :viewport="{ once: true, amount: 0.8 }"
            :transition="{ duration: 1.2, delay: 0.3, ease: [0.16, 1, 0.3, 1] }"
        >
            From market research to internal reviews, we bring all your research into one place so you can go deeper without juggling docs, tabs, and disconnected tools.
        </motion.p>

    </section>
</template>