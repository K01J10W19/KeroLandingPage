<script setup>
    import { motion } from 'motion-v'

    import backgroundImg from '@/assets/images/Cinematic_Background_Img.webp'
</script>

<template>
    <section class="w-full bg-bg-primary py-[var(--spacing-section-y)] flex flex-col items-center relative overflow-hidden font-font-body">
    
        <div class="relative z-10 px-8 flex flex-col items-center">
        
            <motion.h2 
                class="text-white text-center text-4xl md:text-5xl lg:text-[56px] font-font-heading mb-6"
                :initial="{ opacity: 0, y: 30 }"
                :whileInView="{ opacity: 1, y: 0 }"
                :viewport="{ once: true, amount: 0.8 }"
                :transition="{ duration: 0.8, ease: [0.16, 1, 0.3, 1] }"
            >
                Turn research into insight
            </motion.h2>

            <motion.p 
                class="text-white/60 text-center max-w-2xl mx-auto text-sm md:text-base leading-relaxed mb-10"
                :initial="{ opacity: 0, y: 20 }"
                :whileInView="{ opacity: 1, y: 0 }"
                :viewport="{ once: true, amount: 0.8 }"
                :transition="{ duration: 0.8, delay: 0.15, ease: [0.16, 1, 0.3, 1] }"
            >
                A professional workspace designed to support complex research, structured analysis, and reliable insight generation.
            </motion.p>

            <motion.div 
                class="flex flex-wrap items-center justify-center gap-4"
                :initial="{ opacity: 0, y: 20 }"
                :whileInView="{ opacity: 1, y: 0 }"
                :viewport="{ once: true, amount: 0.8 }"
                :transition="{ duration: 0.8, delay: 0.3, ease: [0.16, 1, 0.3, 1] }"
            >
                <button class="px-6 py-2.5 bg-white text-black font-medium text-sm rounded-full transition-transform hover:scale-105">
                    Try for Free
                </button>
                <button class="px-6 py-2.5 bg-[#222] text-white font-medium text-sm rounded-full transition-colors border border-white/5 hover:bg-[#333]">
                    Contact Us
                </button>
            </motion.div>

        </div>

        <motion.div 
            class="w-full max-w-5xl h-[300px] md:h-[450px] mt-12 md:mt-16 relative z-0"
            :initial="{ opacity: 0, scale: 0.95 }"
            :whileInView="{ opacity: 1, scale: 1 }"
            :viewport="{ once: true, amount: 0.3 }"
            :transition="{ duration: 1.5, delay: 0.4, ease: [0.16, 1, 0.3, 1] }"
        >
        <img 
            :src= backgroundImg
            alt="Dark majestic landscape" 
            class="w-full h-full object-cover opacity-50 mix-blend-luminosity"
            style="mask-image: radial-gradient(ellipse 65% 50% at 50% 50%, black 20%, transparent 80%); -webkit-mask-image: radial-gradient(ellipse 65% 50% at 50% 50%, black 20%, transparent 80%);"
        />
        </motion.div>

    </section>
</template>