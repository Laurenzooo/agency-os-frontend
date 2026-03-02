<script setup lang="ts">
const { t } = useI18n();
</script>
<template>
	<div>
		<PortalPageHeader
			:title="t('help.title')"
			:breadcrumbs="[
				{
					title: t('portal.portal'),
					href: '/portal',
				},
				{
					title: t('help.title'),
				},
			]"
		>
			<template #actions></template>
		</PortalPageHeader>
		<HelpCollectionsIndex base-url="/portal" />
	</div>
</template>
