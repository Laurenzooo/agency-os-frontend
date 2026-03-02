<script setup lang="ts">
const { t } = useI18n();
</script>
<template>
	<div>
		<PortalPageHeader
			:title="t('files.title')"
			:breadcrumbs="[
				{
					title: t('portal.portal'),
					href: '/portal',
				},
				{
					title: t('nav.files'),
				},
			]"
		>
			<template #actions>
				<div>
					<PortalFileUploadModal :folder-id="null" />
				</div>
			</template>
		</PortalPageHeader>
		<PortalFilesView :folder-id="null" class="mt-6" />
	</div>
</template>
