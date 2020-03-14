# VueJS-Select2-Component
Simple VueJS select2 component

# Requirement

- [vue(>= 2.0-release)](https://github.com/vuejs/vue)
- [jQuery](https://jquery.com/)
- [select2](https://select2.github.io/)


# Usage
Download the select2 vue component and place it in your VusJS project and import the component
````javascript
import select2 from '/{path-to-select2-component}/select2'
````    
Add select2 component in your template
````html    
<select2 :placeholder="My Select2 Input" :options="options" v-model="selection" :name="select2" class="form-control"></select2>
````    

### Components properties

 - `options`
   Accepts select2 options: `[{id: 1, text: "Value 1"}, {id: 2, text: "Value 2"}]` or `[{text: "Value 1"}, {text: "Value 2"}]`
