<script>
	import {onMount} from 'svelte';
	let cs = ''

	onMount(()=>{
		// type out "coming soon..." with a flashing ibeam 
		let i = 0
		let text = 'coming soon...'
		let interval = setInterval(()=>{
			if(i < text.length){
				cs += text[i]
				i++
			}else{
				clearInterval(interval)
				cs += '<span class="ibeam">|</span>'
			}
		}, 100)
	})

</script>

<div class="w-full h-full flex flex-col justify-center">
	<div class="card w-2/3 h-2/3 mx-auto overflow-hidden">
		<div class="w-full justify-end flex gap-2 pt-4 pb-2 px-4">
			<span class="w-3 h-3 block variant-filled-success rounded-full" />
			<span class="w-3 h-3 block variant-filled-warning rounded-full" />
			<span class="w-3 h-3 block variant-filled-error rounded-full" />
		</div>
		<div class="bg-black w-full h-full rounded p-4">
			{@html cs}
		</div>
	</div>
</div>

<style>
	:global(.ibeam) {	
		animation: blink 1s infinite;
	}
	@keyframes blink {
		0% {
			opacity: 0;
		}
		50% {
			opacity: 1;
		}
		100% {
			opacity: 0;
		}
	}
</style>