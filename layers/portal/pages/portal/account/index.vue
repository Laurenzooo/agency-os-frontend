<script setup lang="ts">
const { t } = useI18n();
</script>
<template>
	<div>
		<PortalPageHeader
			:title="t('account.title')"
			:breadcrumbs="[
				{
					title: t('portal.portal'),
					href: '/portal',
				},
				{
					title: t('account.title'),
				},
			]"
		>
			<template #actions></template>
		</PortalPageHeader>
	</div>
</template>
