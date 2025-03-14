<script lang="ts">
	import { goto } from '$app/navigation';
	import { user } from '$lib/stores';
	import { onMount } from 'svelte';

	onMount(() => {
		if ($user?.role !== 'admin') {
			if ($user?.permissions?.workspace?.models) {
				goto('/openwebui/workspace/models');
			} else if ($user?.permissions?.workspace?.knowledge) {
				goto('/openwebui/workspace/knowledge');
			} else if ($user?.permissions?.workspace?.prompts) {
				goto('/openwebui/workspace/prompts');
			} else if ($user?.permissions?.workspace?.tools) {
				goto('/openwebui/workspace/tools');
			} else {
				goto('/openwebui');
			}
		} else {
			goto('/openwebui/workspace/models');
		}
	});
</script>
