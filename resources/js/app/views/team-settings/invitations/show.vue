<template>
	<div class="content-inner" v-if="show">
		<x-panel margin padding>
			<div slot="title">
				<router-link to="/team-settings/invitations">{{$t('invitation')}}</router-link> / {{model.email}}
			</div>
			<div slot="extra">
				<router-link :to="`/team-settings/invitations`" class="btn btn-default btn-sm">
					<small class="icon icon-arrow-left-c"></small>
				</router-link>
				<x-button size="sm" type="error" icon="trash-b" @click="removeDB('team-settings/invitations', model.id)"></x-button>
			</div>
				<x-row line>
					<x-group col="8" label="email">
						<pre>{{model.email}}</pre>
					</x-group>
					<x-group col="8" label="role">
						<pre>{{model.role.name}}</pre>
					</x-group>
					<x-group col="8" label="created_at">
						<pre>{{model.created_at | toDate}}</pre>
					</x-group>
			</x-row>
		</x-panel>
	</div>
</template>
<script>
	import { showable } from '@js/lib/mixins'

	export default {
		mixins: [ showable ],
		data() {
			return {
				show: false,
				model: {
					permissions: []
				}
			}
		}
	}
</script>