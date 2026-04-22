<script setup>
    import { motion } from 'motion-v'

    import articles_one from '@/assets/images/Cinematic_Background_Img.webp'
    import avatar_one from '@/assets/images/avatar01.webp'
    import articles_two from '@/assets/images/articles02.webp'
    import avatar_two from '@/assets/images/avatar02.webp'
    import articles_three from '@/assets/images/articles03.webp'
    import avatar_three from '@/assets/images/avatar03.webp'
    

    const articles = [
        {
            id: 1,
            image: articles_one,
            imageOverlay: '24M',
            title: 'Kero Raises $24M Series A to Redefine AI Research',
            author: {
                name: 'Mary McDonald',
                avatar: avatar_one
            },
                date: 'Jan 22, 2026'
        },
        {
            id: 2,
            image: articles_two,
            imageOverlay: null, // No overlay text for this one
            title: 'Smarter Research with AI for Modern Teams',
            author: {
                name: 'Jozef Robinson',
                avatar: avatar_two
            },
                date: 'Jan 20, 2026'
        },
        {
            id: 3,
            image: articles_three,
            imageOverlay: 'REPORT #127',
            title: 'January, In Review: Report Generation, Smart Research & More',
            author: {
                name: 'Willow Stewart',
                avatar: avatar_three
            },
                date: 'Jan 2, 2026'
        }
    ]
</script>

<template>
    <section class="w-full bg-bg-primary py-[var(--spacing-section-y)] px-6 sm:px-8 font-sans overflow-hidden">
        <div class="max-w-6xl mx-auto">
        
        <motion.h2 
            class="text-white text-center text-3xl md:text-4xl lg:text-[40px] font-font-heading mb-12 md:mb-16"
            :initial="{ opacity: 0, y: 30 }"
            :whileInView="{ opacity: 1, y: 0 }"
            :viewport="{ once: true, amount: 0.8 }"
            :transition="{ duration: 0.8, ease: [0.16, 1, 0.3, 1] }"
        >
            Our most recent articles
        </motion.h2>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 md:gap-12">
            
            <motion.article 
                v-for="(article, index) in articles" 
                :key="article.id" 
                class="group cursor-pointer flex flex-col"
                :initial="{ opacity: 0, y: 50 }"
                :whileInView="{ opacity: 1, y: 0 }"
                :viewport="{ once: true, amount: 0.2 }"
                :transition="{ duration: 0.8, delay: index * 0.15, ease: [0.16, 1, 0.3, 1] }"
            >
                <div class="relative w-full aspect-[16/10] rounded-2xl overflow-hidden mb-5 bg-[#1a1a1a]">
                    <img 
                        :src="article.image" 
                        :alt="article.title"
                        class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105 opacity-80 mix-blend-luminosity"
                    />
                    
                    <div 
                        v-if="article.imageOverlay" 
                        class="absolute inset-0 flex items-center justify-center bg-black/20"
                    >
                        <span class="text-white text-3xl md:text-4xl font-serif tracking-wide drop-shadow-md">
                            {{ article.imageOverlay }}
                        </span>
                    </div>
                </div>

                <div class="flex flex-col flex-grow">
                    <h3 class="text-white font-bold text-lg md:text-[19px] leading-snug mb-4 transition-colors group-hover:text-white/80">
                        {{ article.title }}
                    </h3>
                    
                    <div class="flex items-center text-[13px] text-white/50 mt-auto">
                        <img 
                            :src="article.author.avatar" 
                            :alt="article.author.name"
                            class="w-5 h-5 rounded-full object-cover mr-2"
                        />
                        <span class="font-medium text-white/70 mr-1.5">{{ article.author.name }}</span>
                        <span class="mr-1.5">·</span>
                        <span>{{ article.date }}</span>
                    </div>
                </div>
            </motion.article>

        </div>
        </div>
    </section>
</template>