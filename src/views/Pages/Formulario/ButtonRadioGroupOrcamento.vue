<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label"
           :class="[{ active: value === option.value }, buttonClasses]">
           
      <input :value="option.value" v-model="model" type="radio" name="option4" autocomplete="off" checked="false" class="form-control">
      {{option.label}}
    </label>
  </div>
</template>
<script>
  export default {
    name: 'button-radio-group-orcamento',
    props: {
      options: {
        type: Array,
        description: 'Radio options',
        default: () => [
          {id:1, value: "70", label: "Até R$70"}
          ,{id:2, value: "100", label: "Até R$100"}
          ,{id:3, value: "150", label: "Até R$150"}
          ,{id:4, value: "outro", label: " Acima de R$150"}
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
      budgetClick(){
        console.log('Olá');
        var inpts = document.getElementsByName("option4");
        var chkds =[];
        inpts.forEach(elem => {
          if(elem.checked){
            chkds.push(elem.parentElement.innerText)
          }
        });
        return chkds;
      }

    }
  }
</script>
<style>
</style>
