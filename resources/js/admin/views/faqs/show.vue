<template>
	<div class="content-inner" v-if="show">
		<x-panel padding>
			<div slot="title">
				<router-link to="/faqs">{{$t('faq')}}</router-link> / {{model.id}}
			</div>
			<div slot="extra">
				<router-link :to="`/faqs`" class="btn btn-default btn-sm">
					<small class="icon icon-arrow-left-c"></small>
				</router-link>
				<router-link :to="`/faqs/${model.id}/edit`" class="btn btn-default btn-sm">
					<small class="icon icon-edit"></small>
				</router-link>
				<x-button size="sm" type="error" icon="trash-b" @click="removeDB('faqs', model.id)"></x-button>
			</div>
			<x-row line>
				<x-group col="12" label="question">
					<pre>{{model.question}}</pre>
				</x-group>
				<x-group col="12" label="answer">
					<pre>{{model.answer}}</pre>
				</x-group>
				<x-group col="8" label="unit_price">
					<p>{{model.show_on_pricing ? $t('yes') : $t('no')}}</p>
				</x-group>
			</x-row>
			<x-row line>
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
					category: {}
				}
			}
		}
	}
</script>