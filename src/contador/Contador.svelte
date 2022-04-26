<script>
	let contador = 0

	function incrementa(){
		contador++
	}

</script>

<div>
	<h2> Contador </h2>
	Valor : {contador}
	<button on:click={incrementa}> Incrementar </button>
	<button on:click={()=>{contador--}}> Decrementar </button>
</div>

<style>
	
button{
	background-color: rgb(40, 40, 138);
	color: white;
}


</style>