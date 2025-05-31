<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label labelRadio"
           :class="[{ active: value === option.value }, buttonClasses]">
           
      <input :value="option.value" v-model="model" type="radio" name="option6" autocomplete="off" checked="false" class="form-control responsiveRadio">
      {{option.label}}
    </label>
  </div>
</template>
<script>
  export default {
    name: 'button-radio-group-almoco',
    props: {
      options: {
        type: Array,
        description: 'Radio options',
        default: () =>  [
          {id:2, value: "115", label: "11h30"}
          ,{id:3, value: "12", label: "12h"}
          ,{id:4, value: "125", label: "12h30"}
          ,{id:1, value: "13", label: "13h"}
          ,{id:5, value: "135", label: "13h30"}
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
      almocoClick(){
        var inpts = document.getElementsByName("option6");
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
