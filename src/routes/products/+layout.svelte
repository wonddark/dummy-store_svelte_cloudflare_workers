<script lang="ts">
	import AppSidebar from '$lib/components/app-sidebar.svelte';
	import { Separator } from '$lib/components/ui/separator/';
	import {
		Inset as SidebarInset,
		Provider as SidebarProvider,
		Trigger as SidebarTrigger
	} from '$lib/components/ui/sidebar';
	import ProductsBreadcrumbs from '$lib/components/products-breadcrumbs.svelte';

	import { page } from '$app/stores';

	const { children } = $props();
</script>

<SidebarProvider>
	<AppSidebar />
	<SidebarInset>
		<header class="flex h-16 shrink-0 items-center gap-2 border-b px-4 sticky top-0 z-50 bg-card text-card-foreground">
			<SidebarTrigger class="-ml-1" />
			<Separator orientation="vertical" class="mr-2 h-4" />
			<ProductsBreadcrumbs route={$page.route.id??''} data={$page.data} />
		</header>
		{@render children()}
	</SidebarInset>
</SidebarProvider>
