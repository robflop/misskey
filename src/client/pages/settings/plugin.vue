<template>
<FormBase>
	<FormLink to="/settings/plugin/install"><template #icon><i class="fas fa-download"></i></template>{{ $ts._plugin.install }}</FormLink>
	<FormLink to="/settings/plugin/manage"><template #icon><i class="fas fa-folder-open"></i></template>{{ $ts._plugin.manage }}<template #suffix>{{ plugins }}</template></FormLink>
</FormBase>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormBase from '@client/components/debobigego/base.vue';
import FormGroup from '@client/components/debobigego/group.vue';
import FormLink from '@client/components/debobigego/link.vue';
import * as os from '@client/os';
import { ColdDeviceStorage } from '@client/store';
import * as symbols from '@client/symbols';

export default defineComponent({
	components: {
		FormBase,
		FormLink,
	},

	emits: ['info'],
	
	data() {
		return {
			[symbols.PAGE_INFO]: {
				title: this.$ts.plugins,
				icon: 'fas fa-plug',
				bg: 'var(--bg)',
			},
			plugins: ColdDeviceStorage.get('plugins').length,
		}
	},

	mounted() {
		this.$emit('info', this[symbols.PAGE_INFO]);
	},
});
</script>

<style lang="scss" scoped>

</style>
