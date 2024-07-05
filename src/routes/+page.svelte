<script lang="ts">
	import SomeWorker from './some-worker?worker';

	async function compute(): Promise<number> {
		const w = new SomeWorker();
		w.postMessage(null);

		return new Promise((resolve) => {
			w.onmessage = (ev: MessageEvent<number>) => resolve(ev.data);
		});
	}
</script>

{#await compute()}
	<p>Now computing...</p>
{:then result}
	<p>Result: {result}</p>
{/await}
