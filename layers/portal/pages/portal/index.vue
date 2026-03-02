<script setup lang="ts">
const { t } = useI18n();

function useGreetings() {
	type Message = string;

	function getTodaysMessage(): Message {
		const messages = t('dashboard.greetings', { returnObjects: true });
		const messagesArray = Array.isArray(messages) ? messages : [];

		// Use the current day as the seed for the message index so that the message stays consistent throughout the day.
		const now = new Date();
		const start = new Date(now.getFullYear(), 0, 0);
		const difference = now.getTime() - start.getTime();
		const oneDay = 1000 * 60 * 60 * 24;
		const dayOfYear = Math.floor(difference / oneDay);
		const messageIndex = dayOfYear % messagesArray.length;

		return messagesArray[messageIndex];
	}

	return {
		getTodaysMessage,
	};
}

const { getTodaysMessage } = useGreetings();
const { user } = useDirectusAuth();
</script>
<template>
	<PageContainer>
		<img class="w-48 ml-auto mr-0" src="~/assets/illustrations/tokyo-luminous-table-lamp-on-boxes.svg" />
		<TypographyTitle class="normal-case">{{ greetUser() }} {{ user?.first_name ?? $t('user.friend') }},</TypographyTitle>
		<TypographyHeadline :content="getTodaysMessage()" size="xl" />
		<VDivider class="my-8" />
		<div class="grid w-full grid-cols-1 gap-6 md:grid-cols-2">
			<PortalInvoiceWidget />
			<PortalTaskWidget />
		</div>
	</PageContainer>
</template>
