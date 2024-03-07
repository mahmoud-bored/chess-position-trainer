<script lang="ts">
    import { onMount } from 'svelte'
    import lightWoodPlate from '$lib/assets/chess-light-wood-plate.png'
    import darkWoodPlate from '$lib/assets/chess-dark-wood-plate.png'
    export let value: string
    export let onClick: (e: Event) => void
    export let bg: "dark" | "light"

    let buttonDark = false
    let buttonLight = false
    onMount(() => {
        if(bg == "dark") {
            buttonDark = true
        } else {
            buttonLight = true
        }
    })
</script>
<button 
    class="w-20 h-10 border border-magnum-600 rounded-md text-white transition cursor-pointer" 
    data-value={value} 
    class:buttonDark
    class:buttonLight
    on:click={onClick}
    >
    {value}
</button>
<style lang="sass">
    button
        position: relative
        z-index: 0
        &:hover
            &::before
                opacity: 1
        &::before
            content: ''
            background-size: cover
            width: inherit
            height: inherit
            position: absolute
            top: -1px
            left: -1px
            border-radius: inherit
            opacity: 0
            transition: all 0.15s ease
            z-index: -1
    .buttonDark
        &::before
            background-image: url('$lib/assets/chess-dark-wood-plate-45deg.png')
    .buttonLight
        &::before
            background-image: url('$lib/assets/chess-light-wood-plate-45deg.png')
</style>