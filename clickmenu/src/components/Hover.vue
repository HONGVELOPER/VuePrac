<template>
    <span @mouseenter="runDelay(true)" @mouseleave="runDelay(false)">
        <slot :hover="hover"></slot>
    </span>
</template>

<script>
export default {
    props: {
        value: {
            type: Boolean,
            default: false,
        },
        disabled: {
            type: Boolean,
            default: false,
        },
        closeDelay: {
            type: [Number, String],
            default: 0,
        },
        openDelay: {
            type: [Number, String],
            default: 0,
        },
    },
    data() {
        return {
            hover: false,
            openTimeout: null,
            closeTimeout: null,
        }
    },
    created() {
        this.hover = this.value
    },
    methods: {
        runDelay(hover) {
            if (this.disabled) return

            clearTimeout(this.openTimeout)
            clearTimeout(this.closeTimeout)
            this[`${hover ? "open" : "close"}Timeout`] = setTimeout(() => {
                this.hover = hover
            }, parseInt(this[`${hover ? "open" : "close"}Delay`]))
        },
    }
}
</script>