<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label labelRadio"
           :class="[{ active: value === option.value }, buttonClasses]">
           
      <input :value="option.value" v-model="model" type="radio" name="option10" autocomplete="off" checked="false" class="form-control responsiveRadio">
      {{option.label}}
    </label>
  </div>
</template>
<script>
  export default {
    name: 'button-radio-group-lanchet',
    props: {
      options: {
        type: Array,
        description: 'Radio options',
        default: () =>  [
          {id:2, value: "15", label: "15h"}
          ,{id:3, value: "155", label: "15h30"}
          ,{id:4, value: "16", label: "16h"}
          ,{id:1, value: "165", label: "16h30"}
          ,{id:5, value: "17", label: "17h"}
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
      lancheTClick(){
        var inpts = document.getElementsByName("option10");
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
