<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label labelRadio"
           :class="[{ active: value === option.value }, buttonClasses]">
           
      <input :value="option.value" v-model="model" type="radio" name="option9" autocomplete="off" checked="false" class="form-control responsiveRadio">
      {{option.label}}
    </label>
  </div>
</template>
<script>
  export default {
    name: 'button-radio-group-lanchem',
    props: {
      options: {
        type: Array,
        description: 'Radio options',
        default: () =>  [
          {id:2, value: "9", label: "9h"}
          ,{id:3, value: "95", label: "9h30"}
          ,{id:4, value: "10", label: "10h"}
          ,{id:1, value: "10", label: "10h30"}
          ,{id:5, value: "11", label: "11h"}
          ,{id:6, value: "nfaz", label: "Não consigo realizar essa refeição"}
          ]
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
      prop: 'value',
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
      lancheMClick(){
        var inpts = document.getElementsByName("option9");
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
