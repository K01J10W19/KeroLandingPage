<script setup>
    import { ref } from 'vue'
    import { motion } from 'motion-v'
    import { Check, ArrowRight, Sparkles } from 'lucide-vue-next'

    const isYearly = ref(true)

    const plans = [
        {
            name: 'Start',
            price: 79,
            description: 'For teams getting started.',
            features: ['Core AI research', 'Multi-source comparison', 'Key insight extraction', 'Structured research workspace', 'Export to PDF and Markdown', 'Email support'],
            highlighted: false
        },
        {
            name: 'Plus',
            price: 149,
            description: 'For teams running research.',
            features: ['Everything in Start, plus:', 'Advanced source synthesis', 'Comparison and analysis', 'Collaboration and workspaces', 'Priority processing for docs', 'Priority support'],
            highlighted: true
        },
        {
            name: 'Ultra',
            price: 229,
            description: 'For teams with ultra needs.',
            features: ['Everything in Plus, plus:', 'Large-scale docs processing', 'Advanced insight and detection', 'Custom templates and workflows', 'API access for internal tools', 'Dedicated support'],
            highlighted: false
        }
    ]

    const containerVariants = {
        hidden: { opacity: 0 },
        visible: {
            opacity: 1,
            transition: { staggerChildren: 0.2, delayChildren: 0.3 }
        }
    }

    const cardVariants = {
        hidden: { opacity: 0, y: 40 },
        visible: { 
            opacity: 1, 
            y: 0, 
            transition: { duration: 0.8, ease: [0.16, 1, 0.3, 1] } 
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
    <section class="relative bg-bg-primary py-[var(--spacing-section-y)] px-8 md:px-16 lg:px-24 overflow-hidden">
        
        <div class="relative z-10 max-w-[1920px] mx-auto">
        
            <header class="text-center mb-16 md:mb-24">
                <motion.h2 
                    class="font-heading text-[clamp(2rem,5vw,3.5rem)] mb-8 text-white"
                    initial="hidden"
                    whileInView="visible"
                    :viewport="{ once: true }"
                    :variants="fadeUp"
                >
                    Simple, scalable pricing
                </motion.h2>
            </header>

            <motion.div 
                class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-stretch"
                :variants="containerVariants"
                initial="hidden"
                whileInView="visible"
                :viewport="{ once: true, amount: 0.1 }"
            >
                <motion.div 
                    v-for="plan in plans" 
                    :key="plan.name"
                    :variants="cardVariants"
                    :class="[
                        'relative p-8 md:p-12 rounded-[2.5rem] border flex flex-col transition-all duration-500',
                        'bg-white/[0.03] backdrop-blur-xl',
                        plan.highlighted 
                            ? 'border-white/30 shadow-[0_32px_64px_-16px_rgba(0,0,0,0.6)]' 
                            : 'border-white/10 hover:border-white/20'
                    ]"
                >
                    <div v-if="plan.highlighted" class="absolute top-4 right-4 md:top-6 md:right-8 w-12 h-12 rounded-full border border-white/20 flex items-center justify-center bg-white/5 backdrop-blur-md">
                        <Sparkles class="w-6 h-6 text-white/60" />
                    </div>

                    <div class="mb-5 md:mb-10">
                        <h3 class="text-white text-sm font-bold uppercase tracking-widest mb-4">
                            {{ plan.name }}
                        </h3>
                        <div class="flex items-baseline gap-1 mb-4">
                            <span class="text-[clamp(2.5rem,4vw,3.5rem)] font-heading text-white tracking-tighter">
                                ${{ isYearly ? plan.price : Math.round(plan.price * 1.2) }}
                            </span>
                            <span class="text-text-muted text-lg">/mo</span>
                        </div>
                            <p class="text-text-muted text-sm font-medium">{{ plan.description }}</p>
                    </div>

                    <div class="w-full h-px bg-white/10 mb-5 border-dashed border-t" />
                    
                    <div class="flex items-center justify-start gap-4">
                        <button 
                            @click="isYearly = !isYearly"
                            :class="[
                            'relative w-14 h-7 rounded-full p-1 transition-all duration-300 cursor-pointer',
                            isYearly ? 'bg-green-500' : 'bg-white/10 hover:bg-white/20'
                            ]"
                        >
                            <motion.div 
                            class="w-5 h-5 bg-white rounded-full shadow-lg"
                            :animate="{ x: isYearly ? 28 : 0 }"
                            :transition="{ type: 'spring', stiffness: 500, damping: 30 }"
                            />
                        </button>
                        
                        <span 
                            :class="[
                            'text-sm font-medium transition-colors duration-300',
                            isYearly ? 'text-white' : 'text-text-muted'
                            ]"
                        >
                            Billed Yearly
                        </span>
                    </div>

                    <div class="w-full h-px bg-white/10 mt-5 mb-10 border-dashed border-t" />

                    <div class="space-y-5 mb-12 flex-grow">
                        <div class="text-[10px] uppercase tracking-[0.2em] font-bold text-white/30 mb-2">Features</div>
                        <div 
                        v-for="feature in plan.features" 
                        :key="feature"
                        class="flex items-start gap-3 group"
                        >
                        <Check class="w-4 h-4 text-white mt-1 shrink-0" />
                        <span class="text-sm text-text-muted leading-relaxed group-hover:text-white transition-colors">
                            {{ feature }}
                        </span>
                        </div>
                    </div>

                    <button 
                        :class="[
                        'w-full py-4 rounded-full font-bold text-sm transition-all duration-300 flex items-center justify-center gap-2 group cursor-pointer',
                        plan.highlighted 
                            ? 'bg-white text-black hover:scale-[1.02] shadow-xl' 
                            : 'bg-white/5 text-white border border-white/10 hover:bg-white/10'
                        ]"
                    >
                        Get Started
                        <ArrowRight class="w-4 h-4 opacity-0 -translate-x-2 group-hover:opacity-100 group-hover:translate-x-0 transition-all" />
                    </button>

                </motion.div>
            </motion.div>
        </div>
    </section>
</template>