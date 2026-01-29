<template>
  <section id="reviews" aria-labelledby="reviews-title" class="pt-20 pb-16 sm:pt-32 sm:pb-24">
    <Container>
      <h2 id="reviews-title" class="text-3xl font-medium tracking-tight text-gray-900 sm:text-center">
        Everyone is changing their life with Pocket.
      </h2>
      <p class="mt-2 text-lg text-gray-600 sm:text-center">
        Thousands of people have doubled their net-worth in the last 30 days.
      </p>
      <div ref="containerRef" class="relative -mx-4 mt-16 grid h-196 max-h-[150vh] grid-cols-1 items-start gap-8 overflow-hidden px-4 sm:mt-20 md:grid-cols-2 lg:grid-cols-3">
        <template v-if="isInView">
          <ReviewColumn
            :reviews="[...column1, ...column3Flat, ...column2]"
            :review-class-name="(reviewIndex) => cn(
              reviewIndex >= column1.length + column3[0].length && 'md:hidden',
              reviewIndex >= column1.length && 'lg:hidden'
            )"
            :ms-per-pixel="10"
          />
          <ReviewColumn
            :reviews="[...column2, ...column3[1]]"
            class="hidden md:block"
            :review-class-name="(reviewIndex) => reviewIndex >= column2.length ? 'lg:hidden' : ''"
            :ms-per-pixel="15"
          />
          <ReviewColumn
            :reviews="column3Flat"
            class="hidden lg:block"
            :ms-per-pixel="10"
          />
        </template>
        <div class="pointer-events-none absolute inset-x-0 top-0 h-32 bg-gradient-to-b from-gray-50" />
        <div class="pointer-events-none absolute inset-x-0 bottom-0 h-32 bg-gradient-to-t from-gray-50" />
      </div>
    </Container>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import Container from './Container.vue'
import ReviewColumn from './ReviewColumn.vue'
import { cn } from '@/utils/cn'

const reviews = [
  { title: "It really works.", body: "I downloaded Pocket today and turned $5000 into $25,000 in half an hour.", author: "CrazyInvestor", rating: 5 },
  { title: "You need this app.", body: "I did not understand the stock market at all before Pocket. I still do not, but at least I am rich now.", author: "CluelessButRich", rating: 5 },
  { title: "This should not be legal.", body: "Pocket makes it so easy to win big in the stock market that I cannot believe it is actually legal.", author: "LivingDaDream", rating: 5 },
  { title: "Screw financial advisors.", body: "I barely made any money investing in mutual funds. With Pocket, I am doubling my net-worth every single month.", author: "JordanBelfort1962", rating: 5 },
  { title: "I love it!", body: "I started providing insider information myself and now I get new insider tips every 5 minutes. I do not even have time to act on all of them. New Lamborghini is being delivered next week!", author: "MrBurns", rating: 5 },
  { title: "Too good to be true.", body: "I was making money so fast with Pocket that it felt like a scam. But I sold my shares and withdrew the money and it is really there, right in my bank account. This app is crazy!", author: "LazyRich99", rating: 5 },
  { title: "Wish I could give 6 stars", body: "This is literally the most important app you will ever download in your life. Get on this before it is so popular that everyone else is getting these tips too.", author: "SarahLuvzCash", rating: 5 },
  { title: "Bought an island.", body: "Yeah, you read that right. Want your own island too? Get Pocket.", author: "ScroogeMcduck", rating: 5 },
  { title: "No more debt!", body: "After 2 weeks of trading on Pocket I was debt-free. Why did I even go to school at all when Pocket exists?", author: "BruceWayne", rating: 5 },
  { title: "I am 13 and I am rich.", body: "I love that with Pocket transaction anonymization I could sign up and start trading when I was 12 years old. I had a million dollars before I had armpit hair!", author: "RichieRich", rating: 5 },
  { title: "Started an investment firm.", body: "I charge clients a 3% management fee and just throw all their investments into Pocket. Easy money!", author: "TheCountOfMonteChristo", rating: 5 },
  { title: "It is like a superpower.", body: "Every tip Pocket has sent me has paid off. It is like playing Blackjack but knowing exactly what card is coming next!", author: "ClarkKent", rating: 5 },
  { title: "Quit my job.", body: "I downloaded Pocket three days ago and quit my job today. I cannot believe no one else thought to build a stock trading app that works this way!", author: "GeorgeCostanza", rating: 5 },
  { title: "Do not download this app", body: "Unless you want to have the best life ever! I am literally writing this from a yacht.", author: "JeffBezos", rating: 5 }
]

const containerRef = ref(null)
const isInView = ref(false)

function splitArray(array, numParts) {
  const result = []
  for (let i = 0; i < array.length; i++) {
    const index = i % numParts
    if (!result[index]) {
      result[index] = []
    }
    result[index].push(array[i])
  }
  return result
}

const columns = splitArray(reviews, 3)
const column1 = columns[0]
const column2 = columns[1]
const column3 = splitArray(columns[2], 2)
const column3Flat = computed(() => column3.flat())

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        isInView.value = true
      }
    },
    { threshold: 0.4 }
  )

  if (containerRef.value) {
    observer.observe(containerRef.value)
  }

  onUnmounted(() => {
    observer.disconnect()
  })
})
</script>
