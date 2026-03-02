<script setup lang="ts">
export interface FileUploadModalProps {
	folderId: string | null | undefined;
}

const props = defineProps<FileUploadModalProps>();
const { t } = useI18n();

const showUploadModal = ref(false);
</script>
<template>
	<UButton icon="material-symbols:upload-file-outline" size="lg" @click="showUploadModal = !showUploadModal">
		{{ t('files.uploadFiles') }}
	</UButton>
	<UModal v-model="showUploadModal">
		<UCard>
			<template #header>
				<TypographyHeadline :content="t('files.uploadFile')" size="xs" />
			</template>
			<VUpload
				:folder-id="folderId"
				multiple
				@success="
					() => {
						showUploadModal = false;
						refreshNuxtData('folder-detail-' + folderId);
					}
				"
			></VUpload>
			<template #footer>
				<div class="flex justify-end gap-x-4">
					<UButton color="primary" @click="showUploadModal = false">{{ t('files.done') }}</UButton>
				</div>
			</template>
		</UCard>
	</UModal>
</template>
