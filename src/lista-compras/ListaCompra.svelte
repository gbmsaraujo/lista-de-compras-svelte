<script>
	import ListaItem from "./ListaItem.svelte";

	let itens = JSON.parse(localStorage.getItem("lista-compras") ?? []);

	let descricao = "";

	function adicionarItem() {
		itens = [
			...itens,
			{
				comprado: false,
				descricao: descricao,
			},
		];
		descricao = "";
	}

	function removeItem(index) {
		itens.splice(index, 1);

		itens = [...itens];

		localStorage.removeItem("itens");
		let itensInJS = JSON.stringify(itens);
		localStorage.setItem("itens", itensInJS);
	}

	$: itensPendentes = itens.filter((item) => !item.comprado).length;

	$: {
		localStorage.setItem("lista-compras", JSON.stringify(itens));
	}
</script>

<h2>Lista de Compras</h2>

<form on:submit|preventDefault={adicionarItem}>
	<!-- Pipes -->
	<input bind:value={descricao} />
	<button type="submit"> Adicionar </button>
</form>

{#if itens.length === 0}
	<p>A Lista Está Vazia!</p>
{:else}
	{#each itens as item, index}
		<ListaItem
			bind:comprado={item.comprado}
			descricao={item.descricao}
			on:itemremovido={() => removeItem(index)}
		/>
	{/each}
{/if}

<div>Itens Pendentes: {itensPendentes}</div>

<style>
</style>
