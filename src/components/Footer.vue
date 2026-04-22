<script setup>
    import { motion } from 'motion-v'
</script>

<template>
    <footer class="w-full bg-bg-primary pt-24 pb-6 px-8 lg:px-12 relative overflow-hidden font-sans border-t border-white/5">
        
        <div class="absolute bottom-0 left-0 right-0 h-[500px] bg-gradient-to-t from-[#6a7c4d]/80 via-[#2d3a1f]/90 to-transparent blur-[120px] pointer-events-none z-0"></div>

        <div class="max-w-7xl mx-auto relative z-10">
        
            <motion.div 
                class="flex flex-col md:flex-row justify-between items-center gap-16 mb-20"
                :initial="{ opacity: 0, y: 30 }"
                :whileInView="{ opacity: 1, y: 0 }"
                :viewport="{ once: true, amount: 0.5 }"
                :transition="{ duration: 0.8, ease: [0.16, 1, 0.3, 1] }"
            >
                <div class="max-w-xs">
                    <div class="w-8 h-8 mb-4 flex items-center">
                        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="w-full h-full text-white">
                            <path d="M12 2L2 7.5L12 13L22 7.5L12 2Z" fill="currentColor"/>
                            <path d="M2 10.5V16L12 21.5L22 16V10.5L12 16L2 10.5Z" fill="currentColor"/>
                        </svg>
                    </div>
                    <p class="text-white/40 text-sm">
                        Structured research, powered by AI.
                    </p>
                </div>

                <div class="grid grid-cols-2 md:grid-cols-3 gap-10 md:gap-16 lg:gap-24">
                
                    <div class="flex flex-col gap-4">
                        <h4 class="text-white/40 text-sm">Resources</h4>
                        <a href="#" class="text-white text-sm font-medium hover:text-white/70 transition-colors">Blog / News</a>
                    </div>

                    <div class="flex flex-col gap-4">
                        <h4 class="text-white/40 text-sm">Utility</h4>
                        <a href="#" class="text-white text-sm font-medium hover:text-white/70 transition-colors">Privacy Policy</a>
                        <a href="#" class="text-white text-sm font-medium hover:text-white/70 transition-colors">Terms</a>
                        <a href="#" class="text-white text-sm font-medium hover:text-white/70 transition-colors">404</a>
                    </div>

                    <div class="flex flex-col gap-4 col-span-2 md:col-span-1">
                        <h4 class="text-white/40 text-sm">Company</h4>
                        <a href="#" class="text-white text-sm font-medium hover:text-white/70 transition-colors">Contact Us</a>
                    </div>

                </div>
            </motion.div>

            <motion.div 
                class="w-full flex justify-center overflow-hidden mb-8 md:mb-12 pointer-events-none select-none"
                :initial="{ opacity: 0, scale: 0.95 }"
                :whileInView="{ opacity: 1, scale: 1 }"
                :viewport="{ once: true, amount: 0.3 }"
                :transition="{ duration: 1.5, delay: 0.2, ease: [0.16, 1, 0.3, 1] }"
            >
                <h1 class="text-[26vw] md:text-[280px] leading-none font-serif tracking-tighter kero-shimmer">
                    Kero
                </h1>
            </motion.div>

            <motion.div 
                class="flex flex-col md:flex-row items-center justify-between gap-6 pt-6 border-t border-white/5"
                :initial="{ opacity: 0 }"
                :whileInView="{ opacity: 1 }"
                :viewport="{ once: true }"
                :transition="{ duration: 0.8, delay: 0.4 }"
            >
                <div class="flex items-center gap-2 text-sm">
                    <span class="text-white/40">Crafted by</span>
                    <img 
                        src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?q=80&w=150&auto=format&fit=crop" 
                        alt="Davide Pacilio" 
                        class="w-5 h-5 rounded-full object-cover grayscale"
                    />
                    <span class="text-white font-medium">Davide Pacilio</span>
                </div>

                <div class="flex items-center text-sm text-white/50">
                    <a href="#" class="hover:text-white transition-colors">X / Twitter</a>
                    <span class="px-3 text-white/20">/</span>
                    <a href="#" class="hover:text-white transition-colors">TikTok</a>
                    <span class="px-3 text-white/20">/</span>
                    <a href="#" class="hover:text-white transition-colors">LinkedIn</a>
                </div>
            </motion.div>

        </div>
    </footer>
</template>

<style scoped>
    /* Custom Shimmer Effect for the Giant Text 
    This creates a metallic, warped gloss look that constantly shifts 
    */
    .kero-shimmer {
        background: linear-gradient(
            110deg,
            #0f0f0f 15%,
            #1a1a1a 30%,
            #333333 48%,
            #5a5a5a 50%,
            #333333 52%,
            #1a1a1a 70%,
            #0f0f0f 85%
        );
        background-size: 250% auto;
        color: transparent;
        -webkit-background-clip: text;
        background-clip: text;
        animation: shine 6s linear infinite;
    }

    @keyframes shine {
        0% {
            background-position: 250% center;
        }
        100% {
            background-position: -50% center;
        }
    }
</style>
