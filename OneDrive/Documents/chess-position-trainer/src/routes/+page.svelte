<script lang="ts">
    import BoardKeyButton from "./BoardKeyButton.svelte";
	import ChessBoard from "./ChessBoard.svelte";

    function handleBoardNumberClick(e: Event) {
        const elmnt = e.target as HTMLButtonElement
        console.log(elmnt.getAttribute('data-value'))
    }
    function handleBoardLetterClick(e: Event) {
        const elmnt = e.target as HTMLButtonElement
        console.log(elmnt.getAttribute('data-value'))
    }
</script>

<section class="w-full h-[100dvh] flex justify-center items-center bg-[#302e2b] text-white">
    <div class="flex justify-center items-center w-3/5">
        <ChessBoard />
    </div>
    <hr class="border-magnum-900 h-full border-[1px]">
    <div class="flex flex-col justify-center items-center w-2/5 h-full gap-3">
        <div class="flex flex-col gap-2 items-center">
            <div class="flex justify-center gap-2 w-full">
                <BoardKeyButton bg="light" value="1" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="dark" value="2" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="light" value="3" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="dark" value="4" onClick={handleBoardNumberClick}/>
            </div>
            <div class="flex justify-center gap-2 w-full">
                <BoardKeyButton bg="dark" value="5" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="light" value="6" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="dark" value="7" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="light" value="8" onClick={handleBoardNumberClick}/>
            </div>
        </div>
        <hr class="w-4/6 border-neutral-600" />
        <div class="flex flex-col gap-2 items-center justify-start">
            <div class="flex justify-center gap-2 w-full">
                <BoardKeyButton bg="light" value="a" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="dark" value="b" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="light" value="c" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="dark" value="d" onClick={handleBoardNumberClick}/>
            </div>
            <div class="flex justify-center gap-2 w-full">
                <BoardKeyButton bg="dark" value="e" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="light" value="f" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="dark" value="g" onClick={handleBoardNumberClick}/>
                <BoardKeyButton bg="light" value="h" onClick={handleBoardNumberClick}/>
            </div>
        </div>
    </div>
</section>