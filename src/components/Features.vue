<script setup>
    import { motion } from 'motion-v'
    import { Link2, Layout, Search, ArrowRight } from 'lucide-vue-next'

    import features01 from '@/assets/images/Linked_Sources.webp'
    import features02 from '@/assets/images/Report_Builder.webp'
    import features03 from '@/assets/images/Search_Insight.webp'


    const features = [
        {
            icon: Link2,
            label: 'Linked Sources',
            title: 'Source Correlation',
            description: 'Explore reports and complex documents with structured extraction, section-level comparison, and clear highlights so teams can review key findings without reading.',
            image: features01
        },
        {
            icon: Layout,
            label: 'Report Builder',
            title: 'Report Generation',
            description: 'Examine lengthy reports and dense docs with guided parsing, side-by-side comparison, and clear highlights so teams can surface key insights without manual review.',
            image: features02
        },
        {
            icon: Search,
            label: 'Search Insights',
            title: 'Research Analysis',
            description: 'Interpret large reports and detailed documents using automated functions, cross-section comparison, and clear highlights so teams can spot what matters without manual review.',
            image: features03
        }
    ]

    // Scroll animation variants
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
    <section class="bg-bg-primary text-text-main py-[var(--spacing-section-y)] px-8 md:px-16 lg:px-24">

        <div class="max-w-[1920px] mx-auto">
            <header class="text-center mb-16 md:mb-32">
                <motion.h2
                    initial="hidden"
                    whileInView="visible"
                    :viewport="{ once: true }"
                    :variants="fadeUp"
                    class="font-heading text-[clamp(2rem,5vw,3.5rem)] mb-6 leading-tight"
                >
                    Deep research for modern work
                </motion.h2>

                <motion.p
                    initial="hidden"
                    whileInView="visible"
                    :viewport="{ once: true }"
                    :variants="fadeUp"
                    class="text-text-muted text-[clamp(1rem,1.5vw,1.25rem)] max-w-2xl mx-auto"
                >
                    Transform complex research into clear insights and confident decision-making.
                </motion.p>
            </header>

            <div class="flex flex-col gap-[var(--spacing-feature-gap)]">
                <div
                    v-for="(feature, index) in features"
                    :key="feature.title"
                    class="flex flex-col gap-12 md:gap-24 items-center rounded-[2rem] border border-white/10 p-8 transition-colors hover:border-white/20"
                    :class="index % 2 === 0 ? 'md:flex-row' : 'md:flex-row-reverse'"
                >
                    <motion.div
                        initial="hidden"
                        whileInView="visible"
                        :viewport="{ once: true, amount: 0.3 }"
                        :variants="fadeUp"
                        class="w-full md:w-1/2 aspect-[4/3] rounded-2xl overflow-hidden bg-bg-primary border-b-0 border-t border-x border-white/10 group relative mb-5 md:mb-0"
                    >
                        <div class="relative w-full h-full">
                            <img
                                :src="feature.image"
                                class="w-full h-full object-cover opacity-70 mix-blend-luminosity"
                            />
                            <div class="absolute inset-x-0 bottom-[-2px] h-2/3 bg-[linear-gradient(to_top,var(--color-bg-primary)_20%,#0a0c0be6_35%,transparent_100%)]"></div>
                        </div>
                    </motion.div>

                    <motion.div
                        initial="hidden"
                        whileInView="visible"
                        :viewport="{ once: true, amount: 0.3 }"
                        :variants="fadeUp"
                        class="w-full md:w-1/2 flex flex-col items-start text-left 3xl:text-center 3xl:items-center"
                    >

                        <div class="flex items-center gap-3 text-text-muted mb-6">
                            <component :is="feature.icon" class="w-5 h-5" />
                            <span class="text-sm font-medium uppercase tracking-widest">{{ feature.label }}</span>
                        </div>

                        <h3 class="font-heading text-[clamp(1.75rem,3vw,2.5rem)] mb-6 leading-snug">
                            {{ feature.title }}
                        </h3>

                        <p class="text-text-muted text-[clamp(1rem,1.2vw,1.15rem)] leading-relaxed mb-10 max-w-lg">
                            {{ feature.description }}
                        </p>

                        <button class="flex items-center gap-2 px-6 py-3 rounded-full border border-white/5 bg-[#1a1a1a] text-[clamp(0.75rem,1.2vw,1.2rem)] font-semibold hover:bg-[#222] hover:text-white transition-all group cursor-pointer">
                            View Pricing & Plans
                            <ArrowRight class="w-4 h-4 group-hover:translate-x-1 transition-transform" />
                        </button>
                    </motion.div>
                </div>
            </div>
        </div>
    </section>
</template>