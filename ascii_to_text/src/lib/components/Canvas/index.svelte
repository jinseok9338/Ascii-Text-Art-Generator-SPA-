<script lang="ts">
    import type {Grid} from "$lib/types/grid"

	export let rows: number;
    export let cols:number;

    $: rowsArray = [...Array(rows).keys()] as number[]
    $: colsArray = [...Array(cols).keys()] as number[]
    let grids = <Grid[]>[] 
    
    
    const toggleSelect=(row:number, col:number) =>{
        const selectedGrid = grids.find((grid) => grid.row == row && grid.col == col )
        if (selectedGrid) {
            grids = grids.filter((grid) => grid.row != row  || grid.col != col)
            return 
        }
        grids = grids.concat([{
            row,
            col,
            letter: "#"
        }])
    }

    $: isSelected =(row:number, col:number) => {
        const selectedGrid = grids.find((grid) => grid.row == row && grid.col == col )
        if (selectedGrid) {
            return true
        }
        return false
    }

    $: console.log(grids)

    const colorArray = ['#FF6633', '#FFB399', '#FF33FF', '#FFFF99', '#00B3E6', 
		  '#E6B333', '#3366E6', '#999966', '#99FF99', '#B34D4D',
		  '#80B300', '#809900', '#E6B3B3', '#6680B3', '#66991A', 
		  '#FF99E6', '#CCFF1A', '#FF1A66', '#E6331A', '#33FFCC',
		  '#66994D', '#B366CC', '#4D8000', '#B33300', '#CC80CC', 
		  '#66664D', '#991AFF', '#E666FF', '#4DB3FF', '#1AB399',
		  '#E666B3', '#33991A', '#CC9999', '#B3B31A', '#00E680', 
		  '#4D8066', '#809980', '#E6FF80', '#1AFF33', '#999933',
		  '#FF3380', '#CCCC00', '#66E64D', '#4D80CC', '#9900B3', 
		  '#E64D66', '#4DB380', '#FF4D4D', '#99E6E6', '#6666FF'];

</script>

<div class="grid-canvas" id="grid-canvas">
    <div class="grid" style={`
    grid-template-columns:repeat(${cols}, 1fr);
    grid-template-rows: repeat(${rows}, 1fr);
    `}>
    {#each rowsArray as row}
        {#each colsArray as col}
            <div
            on:click={()=>{toggleSelect(row,col)}}
             id={`area-${row}-${col}`}
             class="grid-Area"
            style={`grid-area: ${row+1} / ${col+1} / ${row+2} / ${col+2};
                    background-color: ${isSelected(row,col)? colorArray[Math.floor(Math.random()*colorArray.length)]:""}
            `}/>
            
        {/each}
	{/each}
    </div>
</div>

<style>
	.grid-canvas {
        display: flex;
        justify-content: center;
        align-items: center;
		height: 100vh;
		min-width: 300px;
		width: 70%;

	}

    .grid {
        height: 90%;
        width: 90%;
        display: grid;
        grid-column-gap: 0px;
        grid-row-gap: 0px;
        border-top: 1px solid black;
        border-left: 1px solid black;
    }

    .grid-Area {
        border-bottom: 1px solid black;
        border-right: 1px solid black;
    }

    .grid-Area:hover {
        border: 2px solid red;
        cursor: pointer;
    }


</style>
