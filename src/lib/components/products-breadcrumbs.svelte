<script lang="ts">
	import { Item, Link, List, Page, Root, Separator } from '$lib/components/ui/breadcrumb';

	const { route, data }: { route: string, data:Record<string, string> } = $props();
	const routeSegments = route.split('/').filter(item => item);
</script>

<Root>
	<List>
		<Item class="hidden md:block">
			<Link href="/">Home</Link>
		</Item>
		<Separator class="hidden md:block" />
		{#each routeSegments as segment, index}
			{#if index === routeSegments.length - 1}
				<Item>
					<Page>{data.title}</Page>
				</Item>
			{:else}
				<Item class="hidden md:block">
					<Link href="/{segment}">{`${segment.slice(0,1).toUpperCase()}${segment.slice(1)}`}</Link>
				</Item>
				<Separator class="hidden md:block" />
			{/if}
		{/each}

	</List>
</Root>