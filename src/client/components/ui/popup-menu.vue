<template>
<MkPopup ref="popup" :src="src" @closed="$emit('closed')">
	<MkMenu :items="items" :align="align" :width="width" @close="$refs.popup.close()" class="_popup _shadow"/>
</MkPopup>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MkPopup from './popup.vue';
import MkMenu from './menu.vue';

export default defineComponent({
	components: {
		MkPopup,
		MkMenu,
	},

	props: {
		items: {
			type: Array,
			required: true
		},
		align: {
			type: String,
			required: false
		},
		width: {
			type: Number,
			required: false
		},
		viaKeyboard: {
			type: Boolean,
			required: false
		},
		src: {
			required: false
		},
	},

	emits: ['close', 'closed'],
});
</script>
