<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label"
           :class="[{ active: value === option.value }, buttonClasses]">
      
      <input :value="option.value" v-model="model" type="checkbox" id="option2" name="option2" class="form-control">
      {{option.label}}
    </label>
  </div>
</template>
<script>
  export default {
    name: 'button-radio-group',
    props: {
      options: {
        type: Array,
        description: 'Radio options. Should be an array of objects {value: "", label: ""}',
        default: () => [
          {value: "vegano", label: "Vegano"}
          ,{value: "vegetariano", label: "Vegetariano"}
          ,{value: "gluten", label: "Restrição à Glúten"}
          ,{value: "lactose", label: "Restrição à lactose"}
          ,{value: "outro", label: "Outros"}]
      },
      value: {
        type: String,
        description: 'Radio value'
      },
      buttonClasses: {
        type: [String, Object],
        description: 'Inner button css classes'
      }
    },
    model: {
      prop: 'alue',
      event: 'change'
    },
    computed: {
      model: {
        get() {
          return this.value
        },
        set(val) {
          this.$emit('change', val)
        }
      }
    },
    methods: {
      boxClick(){
        var inpts = document.getElementsByName("option2");

        var chkds =[];
        inpts.forEach(elem => {
          if(elem.checked){
            chkds.push(elem.value)
          }
        });
        return chkds;
      }

    } 
  }
</script>
<style>
</style>
