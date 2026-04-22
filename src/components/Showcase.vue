<script setup>
    import { ref } from 'vue'
    import { motion } from 'motion-v'

    import Enterprise_Img from '@/assets/images/enterprise.webp'
    import Marketing_Img from '@/assets/images/marketing.webp'
    import Leadership_Img from '@/assets/images/leadership.webp'
    import ProductIT_Img from '@/assets/images/product_it.webp'
    import Oliver from '@/assets/images/Oliver.webp'


    const tabs = [
        {
            id: 'enterprise',
            label: 'Enterprise',
            image: Enterprise_Img
        },
        {
            id: 'marketing',
            label: 'Marketing',
            image: Marketing_Img
        },
        {
            id: 'leadership',
            label: 'Leadership',
            image: Leadership_Img
        },
        {
            id: 'product-it',
            label: 'Product & IT',
            image: ProductIT_Img
        }
    ]

    const activeTab = ref(tabs[0])

    const features = [
        {
            id: 1,
            title: 'Research Views',
            description: 'A unified view of all documents, sources, and research input.',
            iconType: 'star'
        },
        {
            id: 2,
            title: 'Source Reviews',
            description: 'Analyze and compare information across multiple trusted sources.',
            iconType: 'globe'
        },
        {
            id: 3,
            title: 'Live Highlight',
            description: 'Identify overlaps and contradictions between key links.',
            iconType: 'check'
        },
        {
            id: 4,
            title: 'Auto Summaries',
            description: 'Generate clear structured summaries from complex research.',
            iconType: 'summary'
        },
        {
            id: 5,
            title: 'Insight Finder',
            description: 'Surface key findings, patterns, and signals without review.',
            iconType: 'insight'
        },
        {
            id: 6,
            title: 'Leader Reports',
            description: 'Create structured, decision-ready reports for teams and exec.',
            iconType: 'bolt'
        }
    ]
</script>

<template>
    <section class="w-full bg-bg-primary py-24 flex flex-col items-center px-8 font-sans">
    
        <div class="flex flex-wrap justify-center gap-3 mb-12">
            <button 
                v-for="tab in tabs" 
                :key="tab.id"
                @click="activeTab = tab"
                :class="[
                    'px-5 py-2.5 rounded-full font-medium text-sm transition-all hover:scale-105',
                    activeTab.id === tab.id 
                        ? 'bg-white text-black' 
                        : 'bg-white/10 text-white/70 hover:bg-white/20 hover:text-white'
                ]"
            >
                {{ tab.label }}
            </button>
        </div>

        <motion.div 
            class="relative w-full max-w-5xl aspect-[2/3] md:aspect-[16/9] rounded-3xl overflow-hidden border border-white/10 bg-[#111]"
            :initial="{ opacity: 0, y: 40 }"
            :whileInView="{ opacity: 1, y: 0 }"
            :viewport="{ once: true, amount: 0.2 }"
            :transition="{ duration: 1, ease: [0.16, 1, 0.3, 1] }"
        >
            <Transition name="fade" mode="out-in">
                <img 
                    :key="activeTab.id"
                    :src="activeTab.image" 
                    :alt="activeTab.label + ' background'" 
                    class="absolute inset-0 w-full h-full object-cover mix-blend-luminosity opacity-50"
                />
            </Transition>
            
            <div class="absolute inset-0 bg-gradient-to-b from-black/10 via-transparent to-bg-primary/90"></div>

            <div class="absolute bottom-8 left-1/2 -translate-x-1/2 w-11/12 max-w-2xl text-center pointer-events-none">
                <p class="text-[10px] md:text-xs lg:text-lg text-white/20 font-mono leading-relaxed blur-[0.5px]">
                    technology that lets computers learn things...<br>
                    works in ways that usually require human intelligence...<br>
                    language, recognizing patterns, and...
                </p>
            </div>

            <motion.div 
                :key="'sphere-' + activeTab.id"
                class="absolute top-[20%] left-1/2 -translate-x-1/2 w-10 h-10 md:w-14 md:h-14 rounded-full bg-gradient-to-b from-white via-gray-300 to-gray-500 shadow-[0_0_50px_20px_rgba(255,255,255,0.2)]"
                :initial="{ scale: 0, opacity: 0 }"
                :animate="{ scale: 1, opacity: 1 }"
                :transition="{ delay: 0.4, duration: 1.5, type: 'spring' }"
        ></motion.div>

            <motion.div 
                :key="'card-' + activeTab.id"
                class="absolute top-[45%] left-1/2 -translate-x-1/2 -translate-y-1/2 w-[90%] max-w-[420px] rounded-2xl bg-[#1e1e1e]/60 backdrop-blur-xl border border-white/10 shadow-2xl overflow-hidden"
                :initial="{ y: 50, opacity: 0 }"
                :animate="{ y: '-50%', opacity: 1 }"
                :transition="{ delay: 0.6, duration: 0.8, ease: [0.16, 1, 0.3, 1] }"
            >
                <div class="px-4 py-3 flex items-center border-b border-white/5 bg-white/5">
                    <div class="flex gap-2">
                        <div class="w-2.5 h-2.5 rounded-full bg-white/30"></div>
                        <div class="w-2.5 h-2.5 rounded-full bg-white/30"></div>
                        <div class="w-2.5 h-2.5 rounded-full bg-white/30"></div>
                    </div>
                    <div class="ml-auto w-3 h-0.5 rounded-full bg-white/30"></div>
                </div>

                <div class="px-5 py-4 flex items-center gap-4">
                    
                    <div class="w-12 h-12 rounded-full overflow-hidden border border-white/20 shrink-0">
                        <img 
                            :src= Oliver
                            alt="Oliver" 
                            class="w-full h-full object-cover" 
                        />
                    </div>

                    <div class="flex-1">
                        <div class="flex items-center gap-1.5">
                            <h3 class="text-white font-medium text-[17px]">Oliver</h3>
                            <svg class="w-4 h-4 text-white" viewBox="0 0 24 24" fill="currentColor">
                                <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                            </svg>
                        </div>
                        <p class="text-white/50 text-xs md:text-md mt-0.5">AI Assistant</p>
                    </div>

                    <button class="w-10 h-10 rounded-full bg-white/10 flex items-center justify-center text-white/80 transition-colors hover:bg-white/20 hover:text-white shrink-0">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"/>
                        </svg>
                    </button>
                    
                </div>
            </motion.div>
        </motion.div>
    </section>

    <section class="w-full bg-bg-primary py-24 px-8 font-sans">
        <div class="max-w-7xl mx-auto">
        
            <motion.div 
                class="grid grid-cols-1 md:grid-cols-3 gap-12 text-center"
                :initial="{ opacity: 0 }"
                :whileInView="{ opacity: 1 }"
                :viewport="{ once: true, amount: 0.1 }"
                :transition="{ staggerChildren: 0.15 }"
            >
                <motion.div 
                    v-for="feature in features" 
                    :key="feature.id"
                    class="flex flex-col items-center"
                    :initial="{ opacity: 0, y: 30 }"
                    :transition="{ duration: 0.7, ease: [0.16, 1, 0.3, 1] }"
                    :animate="{ opacity: 1, y: 0 }"
                >
                    <div class="w-14 h-14 rounded-full border border-white/20 flex items-center justify-center mb-6">
                        
                        <div v-if="feature.iconType === 'star'" class="w-7 h-7 relative flex items-center justify-center">
                            <div class="w-5 h-0.5 bg-white/80 absolute"></div>
                            <div class="w-0.5 h-5 bg-white/80 absolute"></div>
                            <div class="w-3.5 h-0.5 bg-white/80 absolute rotate-45"></div>
                            <div class="w-0.5 h-3.5 bg-white/80 absolute rotate-45"></div>
                            <div class="w-1 h-1 bg-white rounded-full absolute"></div>
                        </div>

                        <div v-else-if="feature.iconType === 'globe'" class="w-7 h-7 relative rounded-full border border-white/60">
                            <div class="w-3.5 h-3.5 rounded-full border border-white/80 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"></div>
                            <div class="w-1.5 h-1.5 rounded-full bg-white absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"></div>
                        </div>

                        <div v-else-if="feature.iconType === 'check'" class="w-7 h-7 flex items-center justify-center">
                            <div class="w-5 h-2.5 border-b-2 border-l-2 border-white/80 rotate-[-45deg] mt-[-3px]"></div>
                        </div>

                        <div v-else-if="feature.iconType === 'summary'" class="w-7 h-7 relative flex items-center justify-center">
                            <div class="w-4 h-4 rounded-full border border-white/80 absolute left-0 top-0 opacity-80"></div>
                            <div class="w-4 h-4 rounded-full border border-white/80 absolute right-0 bottom-0 opacity-80"></div>
                            <div class="w-1 h-1 bg-white rounded-full absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"></div>
                        </div>

                        <div v-else-if="feature.iconType === 'insight'" class="w-7 h-7 relative rounded-full border border-white/60">
                            <div class="w-3 h-0.5 bg-white/80 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"></div>
                            <div class="w-0.5 h-3 bg-white/80 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"></div>
                            <div class="w-1 h-1 bg-white rounded-full absolute top-2 right-2"></div>
                        </div>

                        <div v-else-if="feature.iconType === 'bolt'" class="w-7 h-7 relative flex items-center justify-center">
                            <div class="w-3 h-6 bg-white rotate-[15deg] absolute opacity-80" style="clip-path: polygon(100% 0, 0 100%, 100% 100%, 0 0);"></div>
                            <div class="w-3 h-0.5 bg-white absolute left-0 bottom-1 opacity-60"></div>
                            <div class="w-2.5 h-0.5 bg-white absolute left-0 bottom-2.5 opacity-60"></div>
                        </div>

                    </div>

                    <h3 class="text-white font-bold text-[19px] mb-2">{{ feature.title }}</h3>
                    <p class="text-white/50 text-sm leading-relaxed max-w-[340px]">{{ feature.description }}</p>

                </motion.div>
            </motion.div>

        </div>
    </section>
</template>

<style scoped>
    .fade-enter-active,
    .fade-leave-active {
        transition: opacity 0.5s ease;
    }
    .fade-enter-from,
    .fade-leave-to {
        opacity: 0;
    }
</style>