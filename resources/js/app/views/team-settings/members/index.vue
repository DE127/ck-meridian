<template>
	<div class="content-inner">
		<x-filterable :exportable="false" :saved-filters="false"
			:url="url" :sortable="sortable" :filter-group="filters"
			ref="filterable" :title="title">
			<x-tr slot="heading">
			    <x-td type="th" size="4">{{$t('name')}}</x-td>
			    <x-td type="th" size="12">{{$t('email')}}</x-td>
			    <x-td type="th" size="4">{{$t('type')}}</x-td>
			    <x-td type="th" size="4">{{$t('created_at')}}</x-td>
			</x-tr>
			<x-tr slot-scope="{ item }" @click.native="$router.push(`/team-settings/members/${item.id}`)">
			    <x-td>{{item.name}}</x-td>
			    <x-td>{{item.email}}</x-td>
			    <x-td>{{item.type}}</x-td>
			    <x-td>{{item.created_at | toDate}}</x-td>
			</x-tr>
		</x-filterable>
	</div>
</template>
<script>
	import { indexable } from '@js/lib/mixins'
	export default {
		mixins: [indexable],
		data() {
			return {
				url: 'team-settings/members',
				title: 'members'
			}
		},
		computed: {
			sortable() {
				let columns = [
				  'id', 'name', 'created_at'
				]
				return columns
			},
			filters() {
			    let groups = [{
			        title: this.$t('item'),
			        filters: [
			            {name: 'id', type: 'numeric'},
			            {name: 'name', type: 'string'},
			            {name: 'email', type: 'string'},
			            {name: 'created_at', type: 'datetime'},
			        ]
			    }]

			    return groups
			}
		}
	}
</script>