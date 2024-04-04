<script lang="ts">
	import axios from 'axios';

	type JSONValue = string | number | boolean | { [x: string]: JSONValue } | Array<JSONValue>;
	let apiResults: JSONValue;
	const API_URL = 'http://127.0.0.1:8000';

	const instance = axios.create({ baseURL: API_URL });

	const getApi = async () => {
		await instance({ method: 'get', url: '/urls' })
			.then((response) => response.data)
			.then((response) => (apiResults = response));
	};

	const handleClick = () => {
		getApi();
	};

	$: apiResults;
</script>

<p>Shorten your URL</p>
<label>
	URL <input name="URL" />
	<button type="button" class="btn variant-filled" on:click={handleClick}>Send</button>
</label>
<button type="button" class="btn variant-filled" on:click={handleClick}>Get all URLS</button>

<!-- // This is just for showing results -->
{#if apiResults}
	<div>
		{#each apiResults as item, i}
			<li>
				{item.key}: {item.target_url}
			</li>
		{/each}
	</div>
{/if}
<!-- <div>{apiResults ? JSON.stringify(apiResults, null, 2) : ''}</div> -->
<!-- <div>{apiResults ? JSON.stringify(apiResults) : ''}</div> -->
