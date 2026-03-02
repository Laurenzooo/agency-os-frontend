<script setup lang="ts">
const { path, params } = useRoute();
const { t } = useI18n();

const {
	data: project,
	pending,
	error,
} = await useAsyncData(Math.random().toString(36).substring(2, 15), () => {
	return useDirectus(readItem('os_projects', params.id as string));
});

const tabs = computed(() => [
	{
		name: t('projects.overview'),
		href: `/portal/projects/${params.id}`,
	},
	{
		name: t('projects.tasks'),
		href: `/portal/projects/${params.id}/tasks`,
	},
	{
		name: t('projects.conversations'),
		href: `/portal/projects/${params.id}/conversations`,
	},
	{
		name: t('projects.files'),
		href: `/portal/projects/${params.id}/files`,
	},
	{
		name: t('projects.billing'),
		href: `/portal/projects/${params.id}/billing`,
	},
]);
</script>
<template>
	<div class="space-y-6">
		<PortalPageHeader
			:title="project?.name"
			:breadcrumbs="[
				{
					title: t('portal.portal'),
					href: '/portal',
				},
				{
					title: t('projects.title'),
					href: '/portal/projects',
				},
			]"
		>
			<template #center></template>
			<template #actions>
				<div class="inline-flex items-center gap-x-4">
					<VText class="font-semibold" text-color="light">{{ t('projects.targetDate') }}</VText>
					<DateDisplay :date="project?.due_date" size="xs" />
				</div>
			</template>
		</PortalPageHeader>

		<main class="relative">
			<!-- Tabs -->
			<VHorizontalNavigation :items="tabs" />
			<NuxtPage />
		</main>
	</div>
</template>
