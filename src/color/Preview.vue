<template>
    <canvas />
</template>

<script>
import mixin from './mixin'
export default {
    mixins: [mixin],
    props: {
        color: {
            type: String,
            default: '#000000'
        },
        width: {
            type: Number,
            default: 100
        },
        height: {
            type: Number,
            default: 30
        }
    },
    data() {
        return {
            alphaSize: 5
        }
    },
    watch: {
        color() {
            this.renderColor()
        }
    },
    mounted() {
        this.renderColor()
    },
    methods: {
        renderColor() {
            const canvas = this.$el
            const width = this.width
            const height = this.height
            const size = this.alphaSize
            const canvasSquare = this.createAlphaSquare(size)

            const ctx = canvas.getContext('2d')
            canvas.width = width
            canvas.height = height

            ctx.fillStyle = ctx.createPattern(canvasSquare, 'repeat')
            ctx.fillRect(0, 0, width, height)

            ctx.fillStyle = this.color
            ctx.fillRect(0, 0, width, height)
        }
    }
}
</script>
