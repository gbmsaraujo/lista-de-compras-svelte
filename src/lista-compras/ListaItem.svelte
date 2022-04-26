<script>
    import { createEventDispatcher } from "svelte"

    const dispatch = createEventDispatcher()

    export let descricao
    export let comprado
</script>


<div class="ct-itens">
    <label>
        <input type="checkbox" bind:checked={comprado} />
        {descricao}
    </label>
    <button on:click={()=>dispatch("itemremovido")}> Excluir </button>
</div>

<style>
	.ct-itens {
		display: flex;
		align-items: center;
	}

	.ct-itens button {
		margin-left: 10px;
	}
</style>