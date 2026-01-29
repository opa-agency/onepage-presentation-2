<script>
import { defineComponent, h, ref, computed, onMounted, onUnmounted } from 'vue'
import Review from './Review.vue'

export default defineComponent({
  props: {
    reviews: Array,
    className: String,
    reviewClassName: Function,
    msPerPixel: {
      type: Number,
      default: 0
    }
  },
  setup(props) {
    const columnRef = ref(null)
    const columnHeight = ref(0)

    const duration = computed(() => `${columnHeight.value * props.msPerPixel}ms`)
    const doubledReviews = computed(() => [...props.reviews, ...props.reviews])

    onMounted(() => {
      if (!columnRef.value) return

      const resizeObserver = new ResizeObserver(() => {
        columnHeight.value = columnRef.value?.offsetHeight ?? 0
      })

      resizeObserver.observe(columnRef.value)

      onUnmounted(() => {
        resizeObserver.disconnect()
      })
    })

    return () => h('div', {
      ref: columnRef,
      class: `animate-marquee space-y-8 py-4 ${props.className || ''}`,
      style: { '--marquee-duration': duration.value }
    }, 
      doubledReviews.value.map((review, reviewIndex) =>
        h(Review, {
          key: reviewIndex,
          'aria-hidden': reviewIndex >= props.reviews.length,
          className: props.reviewClassName?.(reviewIndex % props.reviews.length),
          ...review
        })
      )
    )
  }
})
</script>

