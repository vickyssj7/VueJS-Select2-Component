# VueJS-Select2-Component
Simple VueJS select2 component

# Requirement

- [vue(>= 2.0)](https://github.com/vuejs/vue)
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

 - `options`:
   - Accepts `Array`
   - Accepts select2 options: `[{id: 1, text: "Value 1"}, {id: 2, text: "Value 2"}]` or `[{text: "Value 1"}, {text: "Value 2"}]`
 - `placeholder`:
   - Accepts `String`
   - Placeholder attribute for your select2 input
 - `multiple`:
   - Accepts: `Boolean`
   - Attribute to Enable or disable select2 multiple options, default is `false`
 - `v-model`:
   - Accepts `String` or `Number` or `Array`
   - Input binding for your select2 component
   - `selection: ''` - `String` or `Number` if multiple is set to false
   - `selection: []` - `Array` if multiple is set to true
 - `name`:
    - Accepts `String`
    - name attribute for your select input
 - `class`:
    - Accepts `String`
    - css class attribute for your select input
 - `disabled`:
    - Accepts `Boolean`
    - prop to disable select2 input
 - `theme`:
    - Accepts `String`
    - prop to add theme for select2
