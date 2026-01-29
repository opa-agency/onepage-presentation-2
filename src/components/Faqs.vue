<template>
  <section
    id="faqs"
    aria-labelledby="faqs-title"
    class="border-t border-gray-200 py-20 sm:py-32"
  >
    <Container>
      <div class="mx-auto max-w-2xl lg:mx-0">
        <h2
          id="faqs-title"
          class="text-3xl font-medium tracking-tight text-gray-900"
        >
          Întrebări frecvente
        </h2>
        <p class="mt-2 text-lg text-gray-600">
          Dacă ai altceva ce vrei să întrebi,{' '}
          <a
            href="mailto:info@example.com"
            class="text-gray-900 underline"
          >
            contactează-ne
          </a>.
        </p>
      </div>
      <ul
        role="list"
        class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-8 sm:mt-20 lg:max-w-none lg:grid-cols-3"
      >
        <li v-for="(column, columnIndex) in faqs" :key="columnIndex">
          <ul role="list" class="space-y-10">
            <li v-for="(faq, faqIndex) in column" :key="faqIndex">
              <h3 class="text-lg/6 font-semibold text-gray-900">
                {{ faq.question }}
              </h3>
              <p class="mt-4 text-sm text-gray-700">{{ faq.answer }}</p>
            </li>
          </ul>
        </li>
      </ul>
    </Container>
  </section>
</template>

<script setup>
import Container from './Container.vue'

const faqs = [
  [
    {
      question: 'Cum știu că sfaturile sunt bune?',
      answer: 'Întreaga noastră afacere depinde de faptul că sfaturile noastre sunt bune, deci este în interesul nostru ca ele să fie. Rezultatele clienților noștri vorbesc de la sine, doar încrede-te în noi.'
    },
    {
      question: 'Nu este asta tranzacționare cu informații privilegiate?',
      answer: 'Da, exact. Dar la scară largă! Istoric, puteai face doar tranzacții cu informații privilegiate cu cunoștințe din rețeaua ta directă. Pocket îți aduce sfaturi de tranzacționare din interior de la oameni pe care nici măcar nu îi cunoști.'
    },
    {
      question: 'Dar nu este tranzacționarea cu informații privilegiate ilegală?',
      answer: 'Iată problema: tu ești cel care face tranzacționarea cu informații privilegiate, nu noi. Noi doar îți dăm sfaturile și câteva instrumente pentru a face tranzacții. Nu facem nimic greșit aici.'
    }
  ],
  [
    {
      question: 'Își dau seama oamenii care vă dau sfaturi ce fac?',
      answer: 'Din nou, aș argumenta că aceasta nu este cu adevărat responsabilitatea noastră. Oamenii fac propriile lor alegeri. Dacă nu cercetează consecințele, e vina lor, nu a noastră.'
    },
    {
      question: 'Unde este bazat Pocket?',
      answer: 'Să zicem doar că nu este undeva unde SEC ne va găsi.'
    },
    {
      question: 'Există vreo limită de vârstă pentru tranzacționarea pe Pocket?',
      answer: 'Pentru planul nostru gratuit, limita de vârstă se bazează pe vârsta minimă pentru tranzacționare în țara ta de reședință. Planul nostru VIP folosește anonimizare avansată a tranzacțiilor, așa că poți folosi acel plan chiar dacă ai 9 ani. Sau ești un câine.'
    }
  ],
  [
    {
      question: 'Cum ați reușit să puneți asta pe App Store?',
      answer: 'Sincer, am fost surprinși și noi, dar în cele din urmă am aflat că recenzentul de aplicații a găsit aplicația att de convingtoară încât a aprobat-o doar ca să o poată folosi ei înșiși.'
    },
    {
      question: 'Cum explic banii pe care îi retrag din Pocket la fisc?',
      answer: 'Aceasta pare a fi o sută la sută problema ta. Pocket nu este responsabil în niciun fel pentru declarațiile tale fiscale.'
    },
    {
      question: 'Cum devin un insider?',
      answer: 'Contactează-ne cu câteva detalii despre industria ta și tipul de acces pe care îl ai pentru a aplica pentru un cont de insider. Odată aprobat, îți vom trimite un ghid despre cum să colectezi informații din interior fără a fi detectat la serviciu.'
    }
  ]
]
</script>
