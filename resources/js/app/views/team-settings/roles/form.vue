<template>
	<div class="content-inner" v-if="show">
		<x-panel margin padding>
			<div slot="title">{{$t(mode)}} {{$t('role')}}</div>
			<x-row line>
				<x-form-group col="8" v-model="form.name" :label="$t('name')" :errors="errors.name"></x-form-group>
				<x-form-group col="8" source="textarea" v-model="form.description" :label="$t('description')" :errors="errors.description"></x-form-group>
			</x-row>
		</x-panel>
		<x-panel padding>
			<div slot="title">{{$t('permissions')}}</div>
			<div>
				<x-row v-for="(actions, name) in form.permissions.modules" :key="name" line>
					<x-group col="24" :label="name">
						<x-row>
							<x-col span="8" v-for="(value, key) in actions" :key="key">
								<label class="permission">
									<span class="permission-icon">
										<input type="checkbox" v-model="actions[key]">
									</span>
									<span class="permission-text">{{$t(key)}}</span>
								</label>
							</x-col>
						</x-row>
					</x-group>
				</x-row>
				<x-row line>
					<x-group col="24" label="Team Settings">
						<x-row>
							<x-col span="8" v-for="(value, key) in form.permissions.settings" :key="key">
								<label class="permission">
									<span class="permission-icon">
										<input type="checkbox" v-model="form.permissions.settings[key]">
									</span>
									<span class="permission-text">{{$t(key)}}</span>
								</label>
							</x-col>
						</x-row>
					</x-group>
				</x-row>
			</div>
			<div slot="footer" class="flex flex-end">
				<div>
					<x-button @click="cancel" :disabled="isSaving">{{$t('cancel')}}</x-button>
					<x-button @click="save" type="primary" :loading="isSaving">{{$t('save')}}</x-button>
				</div>
			</div>
		</x-panel>
	</div>
</template>
<script>
	import { formable } from '@js/lib/mixins'
	export default {
		mixins: [ formable ],
		data() {
			return {
				form: {
					permissions: []
				},
				redirect: 'team-settings/roles'
			}
		}
	}
</script>