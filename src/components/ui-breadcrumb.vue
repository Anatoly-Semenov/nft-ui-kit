<template>
	<div class="ui-breadcrumb" :class="{ _loading: isLoading }">
		<button
			class="ui-breadcrumb__back"
			v-if="showArrow"
			@click="$emit('returnBack')"
		>
			<ui-icon iconType="ant-design" type="left" />
		</button>
		<a-breadcrumb :separator="separator">
			<a-breadcrumb-item
				v-for="({ action, route }, index) in crumbs"
				:key="index + 'crumb'"
			>
				<button @click="action(crumbs, index)" v-if="route">
					{{ route }}
				</button>
			</a-breadcrumb-item>
		</a-breadcrumb>
	</div>
</template>
<script lang="ts">
import Vue, { PropOptions } from "vue"

// Use Ant-component
import { Breadcrumb } from "../libs/ant-design-vue"
Vue.use(Breadcrumb)

// Interfaces
import { UiBreadcrumb } from "../types"

export default Vue.extend({
	name: "ui-breadcrumb",

	props: {
		showArrow: {
			type: Boolean,
			default: true
		} as PropOptions<boolean>,
		separator: {
			type: String,
			default: "/"
		} as PropOptions<string>,
		crumbs: Array as PropOptions<UiBreadcrumb.Crumb>,
		isLoading: Boolean as PropOptions<boolean>
	}
})
</script>
