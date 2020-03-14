<template>
	<select :placeholder="placeholder" :multiple="multiple" :name="name">
		<option v-if="!multiple" value ="-1" disabled selected>{{placeholder}}</option>
	</select>
</template>
<script>
let option = [];
export default {
	props: {
		placeholder: {
			type: String,
			default: ''
		},
		name: {
			type: String,
			default: ''
		},
		options: {
			type: Array,
			default: []
		},
		multiple: {
			type: Boolean,
			default: false
		},
		disabled: {
			type: Boolean,
			default: false
		},
		settings: Object,
		theme: {
			type: String,
			default: ''
		},
		defaultSettings: {
			type: Object,
			default: function() {
				return {
					placeholder: this.placeholder,
					data: this.options
				}
			}
		},
		value: [Array, String, Number]
	},
	watch: {
		value: function(value) {
			option = value;
		},
		options: function() {
			var getVals;
			if(this.multiple) {
				getVals = this.value.map(function(val) {
					return val.toString();
				});
			} else {
				getVals = this.value.toString();
			}
			option = getVals;
			$(this.$el).select2({...this.defaultSettings}).val(this.value).trigger("change");
		}
	},
	mounted: function() {
		var elm = $(this.$el), vm = this;
		elm.select2({
			name: this.name,
			placeholder: this.placeholder,
			multiple: this.multiple,
			disabled: this.disabled,
			theme: this.theme,
			data: this.options,
			...this.settings
		})
		.on("select2:select", (e) => vm.selectedOption(e))
		.on("select2:unselect", (e) => vm.unselectedOption(e))
		.on("change", (e) => vm.selectionChange(e, vm));
	},
	methods: {
		selectedOption(e) {
			if(this.multiple) {
				option.push(e.params.data.id);
			} else {
				option = e.params.data.id;
			}
		},
		unselectedOption(e) {
			if(this.multiple) {
				option.push(e.params.data.id);
				delete option[option.indexOf(e.params.data.id)];
				option = option.filter(val => val > 0);
			} else {
				option = e.params.data.id;
			}
		},
		selectionChange(e, vm) {
			if(!this.multiple) {
				option = '';
				option = e.target.value;
			}
			vm.$nextTick(function() {
				vm.$emit("input", option);
				console.log(option);
			})
		}
	},
	destroyed: function() {
		$(this.$el).off().select2("destroy");
	}
};
</script>