<script setup>
    import { motion, AnimatePresence } from 'motion-v';
    import { ShoppingCart, Plus, Check, Info, X } from 'lucide-vue-next';
    import { ref } from 'vue';

    const selectedPlan = ref('Plus')
    const plans = ['Start', 'Plus', 'Ultra']

    const features = [
        { label: 'Workspaces', start: 'Unlimited', plus: 'Unlimited', ultra: 'Unlimited' },
        { label: 'Team members', start: '10 seats / mo', plus: '25 seats / mo', ultra: '99 seats / mo', info: true },
        { label: 'Custom AI templates', start: true, plus: true, ultra: true },
        { label: 'API access', start: true, plus: true, ultra: true },
        { label: 'White labeling', start: true, plus: true, ultra: true },
        { label: 'AI generations', start: true, plus: true, ultra: true },
        { label: 'Security', start: true, plus: true, ultra: true },
        { label: 'Data protection', start: true, plus: true, ultra: true },
        { label: 'References', start: true, plus: true, ultra: true },
        { label: 'Chat with Paper/PDF', start: false, plus: true, ultra: true },
        { label: 'Data extraction', start: false, plus: false, ultra: true },
        { label: 'Plagiarism check', start: false, plus: false, ultra: true },
    ]

    const containerVariants = {
        hidden: { opacity: 0 },
        visible: {
            opacity: 1,
            transition: {
            staggerChildren: 0.15, // Sequential pop-up delay
            },
        },
    };

    const cardFade = {
        hidden: { opacity: 0, scale: 0.9, y: 30 },
        visible: {
            opacity: 1,
            scale: 1,
            y: 0,
            transition: {
                duration: 0.8, // Slightly faster, clean pop
                ease: [0.16, 1, 0.3, 1], // Sleek ease
            },
        },
    };

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
    <section class="bg-bg-primary py-[var(--spacing-section-y)] px-8 md:px-16 lg:px-24 overflow-hidden">
        <div class="max-w-[1920px] mx-auto">
        
        <header class="text-center mb-20 md:mb-32 px-4">
            <motion.h2 
            class="font-heading text-[clamp(2.5rem,5vw,4.5rem)] text-white mb-12 leading-tight"
            initial="hidden"
            whileInView="visible"
            :viewport="{ once: true }"
            :variants="fadeUp"    
            >
            Plans and Features
            </motion.h2>

            <motion.div 
            class="lg:hidden flex w-full max-w-[300px] sm:max-w-max mx-auto p-1 bg-white/5 rounded-full border border-white/10 mb-12"
            initial="hidden"
            whileInView="visible"
            :viewport="{ once: true }"
            :variants="fadeUp"
            >
            <button 
                v-for="plan in plans" 
                :key="plan"
                @click="selectedPlan = plan"
                class="relative flex-1 sm:flex-none px-2 sm:px-10 py-2.5 text-xs sm:text-sm font-bold transition-colors"
                :class="selectedPlan === plan ? 'text-black' : 'text-text-muted'"
            >
                <span class="relative z-10">{{ plan }}</span>
                <motion.div 
                v-if="selectedPlan === plan"
                layoutId="activePlan"
                class="absolute inset-0 bg-white rounded-full z-0"
                :transition="{ type: 'spring', stiffness: 500, damping: 35 }"
                />
            </button>
            </motion.div>
        </header>

        <div class="relative mt-20 md:mt-28">
            
            <div class="grid grid-cols-2 lg:grid-cols-4 items-stretch relative z-10">
                
                <div class="lg:hidden col-span-1 py-8 border-b border-white/10">
                    <span class="text-[10px] font-bold text-white/40 uppercase tracking-widest">Feature</span>
                </div>
                <div class="lg:hidden col-span-1 py-8 border-b border-white/10 text-right">
                    <span class="text-[10px] font-bold text-white uppercase tracking-widest">{{ selectedPlan }}</span>
                </div>

                <div class="hidden lg:block h-32" /> 

                <div 
                    v-for="plan in plans" 
                    :key="plan"
                    :class="[
                    'hidden lg:flex flex-col items-center justify-end pb-8 relative',
                    ]"
                >
                    <div class="absolute bottom-0 w-24 border-t border-dashed border-white/20" />
                    <span class="font-bold text-white tracking-[0.25em] uppercase text-[10px] md:text-xs mb-4">
                        {{ plan }}
                    </span>
                </div>

                <template v-for="feature in features" :key="feature.label">
                    
                    <div class="col-span-1 lg:col-span-1 py-6 flex items-center gap-2 border-b border-white/5">
                        <span class="text-xs md:text-sm 2xl:text-lg font-medium text-text-muted">
                            {{ feature.label }}
                        </span>
                        <Info v-if="feature.info" class="w-3.5 h-3.5 text-white/20 cursor-help" />
                    </div>

                    <div 
                        v-for="plan in plans" 
                        :key="plan"
                        :class="[
                            'py-5 flex items-center border-b border-white/5 transition-all duration-500',
                            selectedPlan === plan ? 'col-span-1 justify-center' : 'hidden lg:flex lg:justify-center',
                            /* Subtle column highlight for mobile active plan */
                            plan === 'Plus' && selectedPlan === 'Plus' ? 'bg-white/[0.02] lg:bg-transparent' : ''
                        ]"
                    >
                        <template v-if="typeof feature[plan.toLowerCase()] === 'boolean'">
                            <Check v-if="feature[plan.toLowerCase()]" class="w-4 h-4 2xl:w-6 2xl:h-6 text-white opacity-90" />
                            <X v-else class="w-4 h-4 2xl:w-6 2xl:h-6 text-white/10" />
                        </template>
                        
                        <span v-else class="text-[10px] md:text-xs 2xl:text-base font-bold text-white/70">
                            {{ feature[plan.toLowerCase()] }}
                        </span>
                    </div>
                </template>

                <div class="hidden lg:block py-16" /> 

                <div 
                    v-for="plan in plans" 
                    :key="plan"
                    :class="[
                    'py-12 justify-center transition-all duration-500',
                    selectedPlan === plan ? 'flex col-span-2' : 'hidden',
                    'lg:flex lg:col-span-1'
                    ]"
                >
                    <button 
                        :class="[
                            'w-full lg:w-[180px] py-4 rounded-full text-[10px] font-bold uppercase tracking-widest transition-all',
                            plan === 'Plus' ? 'bg-white text-black shadow-[0_0_40px_rgba(255,255,255,0.3)] scale-105 hover:scale-110' : 'bg-white/10 text-white border border-white/5 hover:bg-white/20'
                        ]"
                    >
                        Get Started
                    </button>
                </div>

            </div>

            <motion.div 
                class="hidden lg:block absolute top-5 bottom-10 left-[50%] w-[25%] z-0 pointer-events-none"
                initial="{ opacity: 0, scaleY: 0.9 }"
                whileInView="{ opacity: 1, scaleY: 1 }"
                :viewport="{ once: true }"
                :transition="{ duration: 1.2, ease: [0.16, 1, 0.3, 1], delay: 0.2 }"
            >
                <div class="w-full h-full bg-white/[0.03] border border-white/20 rounded-[3rem] backdrop-blur-3xl shadow-[0_50px_100px_-20px_rgba(0,0,0,0.8)]">
                    
                    <div class="absolute -top-5 left-1/2 -translate-x-1/2 flex flex-col items-center">
                        <div class="px-10 py-1.5 bg-white text-black text-[10px] font-bold uppercase tracking-[0.2em] rounded-full shadow-xl">
                            Best Value
                        </div>
                        <div class="w-0 h-0 border-l-[6px] border-l-transparent border-r-[6px] border-r-transparent border-t-[6px] border-t-white" />
                    </div>

                </div>
            </motion.div>

        </div>
        </div>
    </section>
</template>