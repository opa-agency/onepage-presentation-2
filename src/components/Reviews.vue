<template>
  <section id="reviews" aria-labelledby="reviews-title" class="pt-20 pb-16 sm:pt-32 sm:pb-24">
    <Container>
      <h2 id="reviews-title" class="text-3xl font-medium tracking-tight text-gray-900 sm:text-center">
        Toată lumea își schimbă viața cu Pocket.
      </h2>
      <p class="mt-2 text-lg text-gray-600 sm:text-center">
        Mii de oameni și-au dublat averea netă în ultimele 30 de zile.
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
  { title: "Chiar funcționează.", body: "Am descărcat Pocket astăzi și am transformat 5000$ în 25.000$ în jumătate de oră.", author: "InvestitorNebun", rating: 5 },
  { title: "Ai nevoie de această aplicație.", body: "Nu am înțeles deloc piața de acțiuni înainte de Pocket. Tot nu o înțeleg, dar cel puțin sunt bogat acum.", author: "ConfuzDarBogat", rating: 5 },
  { title: "Asta nu ar trebui să fie legal.", body: "Pocket face att de ușor să câștigi mare pe piața de acțiuni încât nu pot crede că este de fapt legal.", author: "TraiescVisul", rating: 5 },
  { title: "La naiba cu consilierii financiari.", body: "Am câștigat puțini bani investind în fonduri mutuale. Cu Pocket, îmi dublez averea netă în fiecare lună.", author: "JordanBelfort1962", rating: 5 },
  { title: "Iubesc asta!", body: "Am început să furnizez eu însumi informații din interior și acum primesc noi sfaturi la fiecare 5 minute. Nici măcar nu am timp să acționez asupra tuturor. Noul Lamborghini este livrat săptămâna viitoare!", author: "DlBurns", rating: 5 },
  { title: "Prea bun ca să fie adevărat.", body: "Făceam bani att de repede cu Pocket încât părea o înșelătorie. Dar mi-am vândut acțiunile și am retras banii și sunt cu adevărat acolo, chiar în contul meu bancar. Această aplicație este nebună!", author: "LeneBogat99", rating: 5 },
  { title: "Aș vrea să pot da 6 stele", body: "Aceasta este literalmente cea mai importantă aplicație pe care o vei descărca vreodată în viața ta. Ia-o înainte să fie att de populară încât toată lumea să primească aceste sfaturi.", author: "SaraIubescBanii", rating: 5 },
  { title: "Am cumpărat o insulă.", body: "Da, ai citit corect. Vrei și tu propria insulă? Ia-ți Pocket.", author: "ScroojeMcduck", rating: 5 },
  { title: "Fără mai multe datorii!", body: "După 2 săptămâni de tranzacționare pe Pocket eram fără datorii. De ce am mai fost la școală când există Pocket?", author: "BruceWayne", rating: 5 },
  { title: "Am 13 ani și sunt bogat.", body: "Iubesc faptul că cu anonimizarea tranzacțiilor Pocket m-am putut înscrie și începe să tranzacționez când aveam 12 ani. Aveam un milion de dolari înainte să am păr la subraț!", author: "BogatBogatash", rating: 5 },
  { title: "Am început o firmă de investiții.", body: "Tax clienții cu un comision de management de 3% și arunc toate investițiile lor în Pocket. Bani ușori!", author: "ConteleDeMonteCristo", rating: 5 },
  { title: "Este ca o superputere.", body: "Fiecare sfat pe care mi l-a trimis Pocket s-a rentabilizat. Este ca și cum ai juca Blackjack dar știi exact ce carte urmează!", author: "ClarkKent", rating: 5 },
  { title: "Mi-am dat demisia.", body: "Am descărcat Pocket acum trei zile și mi-am dat demisia astăzi. Nu pot crede că nimeni altcineva nu s-a gândit să construiască o aplicație de tranzacționare care funcționează în acest fel!", author: "GeorgeCostanza", rating: 5 },
  { title: "Nu descărca această aplicație", body: "Doar dacă nu vrei să ai cea mai bună viață vreodată! Scriu asta literalmente de pe un iaht.", author: "JeffBezos", rating: 5 }
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
