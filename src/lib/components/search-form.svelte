<script lang="ts">
	import { Label } from '$lib/components/ui/label/index.js';
	import type { WithElementRef } from 'bits-ui';
	import Search from 'lucide-svelte/icons/search';
	import type { HTMLFormAttributes } from 'svelte/elements';
	import { Group, GroupContent, Input } from '../components/ui/sidebar';

	let { ref = $bindable(null), ...restProps }: WithElementRef<HTMLFormAttributes> = $props();
</script>

<form bind:this={ref} {...restProps}>
	<Group class="py-0">
		<GroupContent class="relative">
			<Label for="search" class="sr-only">Search</Label>
			<Input id="search" placeholder="Search the docs..." class="pl-8" />
			<Search
				class="pointer-events-none absolute left-2 top-1/2 size-4 -translate-y-1/2 select-none opacity-50"
			/>
		</GroupContent>
	</Group>
</form>
