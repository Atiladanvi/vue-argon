<template>
	<div :class="`bg-${type}`" class="card card-stats mb-4 mb-lg-0">
		<div class="card-body">
			<div class="row">
				<div class="col">
					<h5 :class="color(type)" class="card-title text-uppercase mb-0">{{ title }}</h5>
					<span
						:class="color(type)"
						class="h2 font-weight-bold mb-0">
							<animated-number
								:value="value"
								:formatValue="formatValue"
								:duration="3000"
							/>
						</span>
				</div>
				<div class="col-auto">
					<div
						v-if="icon.class"
						:class="`${colorIcon(icon.background)} bg-${icon.background}`"
						class="icon icon-shape rounded-circle shadow"
					>
						<i :class="icon.class"></i>
					</div>
				</div>
			</div>
			<p class="mt-3 mb-0 text-muted text-sm">
					<span
						v-if="hint.value"
						:class="`text-${hint.color}`"
						class="mr-2">
						<i :class="`${hint.icon}`"></i> {{ formatHintValue(hint.value)}}
					</span>
				<span :class="color(type)" class="text-nowrap">{{ description }}</span>
			</p>
		</div>
	</div>
</template>

<script>
import AnimatedNumber from "animated-number-vue";
export default {
	name: "Widget",
	components: {
		AnimatedNumber
	},
	props:{
    format: {
			type: String,
			default: ''
		},
		decimalSeparator: {
			type: String,
			default: '.'
		},
		title: {
			type: String,
			default: 'Title'
		},
		description: {
			type: String,
			default: 'description'
		},
		value: {
			type: String,
			default: '000,00'
		},
		toFixe: {
			type: Number,
			default: 0
		},
		icon: {
			type: Object,
			default(){
				return {
					class: '',
					background:'white',
				}
			}
		},
		hint:{
			type: Object,
			default() {
				return {
					value: '',
					icon: '',
					toFixe: 2,
					format: '',
					color: 'white'
				}
			}
		},
		type:{
			type: String,
			default: 'default'
		},
	},
	methods:{
		formatValue(value) {
			return `${value.toFixed(this.toFixe).toString().replace("." , `${this.decimalSeparator}`)} ${this.format || ''}`;
		},
		formatHintValue(value) {
			return `${parseFloat(value).toFixed(this.hint.toFixe).toString().replace("." , `${this.decimalSeparator}`)} ${this.hint.format || ''}`;
		},
		color: function (type) {
			switch (type) {
				case 'white':
					return 'text-dark';
				break;
				case 'secondary':
					return 'text-dark';
				break;
				default:
					return 'text-white'
			}
		},
		colorIcon: function (type) {
			switch (type) {
				case 'white':
					return 'text-dark';
				break;
				case 'success':
					return 'text-dark';
				break;
				default:
					return 'text-white'
			}
		}
	},
}
</script>
