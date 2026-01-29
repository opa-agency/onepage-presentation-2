<script>
import { defineComponent, h, computed } from 'vue'

const StarIcon = (props) => h('svg', { viewBox: '0 0 20 20', 'aria-hidden': 'true', ...props }, [
  h('path', { d: 'M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z' })
])

const StarRating = defineComponent({
  props: {
    rating: Number
  },
  setup(props) {
    return () => h('div', { class: 'flex' }, 
      [...Array(5).keys()].map((index) =>
        h(StarIcon, {
          key: index,
          class: props.rating > index ? 'h-5 w-5 fill-cyan-500' : 'h-5 w-5 fill-gray-300'
        })
      )
    )
  }
})

export default defineComponent({
  props: {
    title: String,
    body: String,
    author: String,
    rating: Number,
    className: String
  },
  setup(props) {
    const possibleAnimationDelays = ['0s', '0.1s', '0.2s', '0.3s', '0.4s', '0.5s']
    const animationDelay = possibleAnimationDelays[Math.floor(Math.random() * possibleAnimationDelays.length)]

    return () => h('figure', {
      class: `animate-fade-in rounded-3xl bg-white p-6 opacity-0 shadow-md shadow-gray-900/5 ${props.className || ''}`,
      style: { animationDelay }
    }, [
      h('blockquote', { class: 'text-gray-900' }, [
        h(StarRating, { rating: props.rating }),
        h('p', { class: 'mt-4 text-lg/6 font-semibold text-gray-900' }, `"${props.title}"`),
        h('p', { class: 'mt-3 text-base/7 text-gray-900' }, props.body)
      ]),
      h('figcaption', { class: 'mt-3 text-sm text-gray-600' }, `– ${props.author}`)
    ])
  }
})
</script>

