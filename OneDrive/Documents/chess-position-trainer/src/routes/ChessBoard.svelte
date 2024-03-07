<script lang="ts">
	import { onMount } from "svelte";

    const boardNumbers = [1, 2, 3, 4, 5, 6, 7, 8]
    const boardLetters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']

    function isEven(n: number) {
        return n % 2 === 0;
    }
    function isOdd(n: number) {
        return n % 2 !== 0;
    }
    function applyTileStyles(rowIndex: number, columnIndex: number, style: "dark" | "light") {
        if(rowIndex !== 0 && rowIndex !== 1 && rowIndex !== 6 && rowIndex !== 7) {
            if(style == "dark") {
                document.querySelector(`[data-row="${boardNumbers[rowIndex]}"][data-col="${boardLetters[columnIndex]}"]`)?.classList.add('dark-tile')
            } else if(style == "light") {
                document.querySelector(`[data-row="${boardNumbers[rowIndex]}"][data-col="${boardLetters[columnIndex]}"]`)?.classList.add('light-tile')
            }
        }
    }
    onMount(() => {
        for(let i = 0; i < boardLetters.length; i++) {
            for(let j = 0; j < boardNumbers.length; j++) {
                if(isEven(i)) {
                    if(isOdd(j)) {
                        applyTileStyles(i, j, "dark")
                    } else {
                        applyTileStyles(i, j, "light")
                    }
                } else {
                    if(isOdd(j)) {
                        applyTileStyles(i, j, "light")
                    } else {
                        applyTileStyles(i, j, "dark")
                    }
                }
            }
        }
    })
</script>

<div class="rotate-180 grid grid-cols-[repeat(8,_minmax(40px,_1fr))] grid-rows-[repeat(8,_minmax(40px,_1fr))] gap-3 bg-[#36481d] p-4 rounded-lg">
    {#each boardNumbers as boardRow}
        {#each boardLetters as boardColumn, i} 
            <button class="chessboard-button rounded-lg bg-magnum-900 aspect-square w-full h-full" data-col={boardColumn} data-row={boardRow}></button>
        {/each}
    {/each}
</div>
<style lang="sass">
    .chessboard-button[data-row="1"],
    .chessboard-button[data-row="2"]
        background-color: white !important

    .chessboard-button[data-row="7"],
    .chessboard-button[data-row="8"]
        background-color: black !important
    :global(.dark-tile)
        background-image: url('$lib/assets/chess-dark-wood-plate.png')
        background-size: cover
    :global(.light-tile)
        background-image: url('$lib/assets/chess-light-wood-plate.png')
        background-size: cover
</style>