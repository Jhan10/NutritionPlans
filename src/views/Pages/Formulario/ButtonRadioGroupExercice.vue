<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label labelRadio"
           :class="[{ active: value === option.value }, buttonClasses]">
           
      <input :value="option.value" v-model="model" type="radio" name="option3" autocomplete="off" checked="false" class="form-control responsiveRadio">
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
        description: 'Radio options',
        default: () => [
          {id:1, value: "sedentario", label: "Sedentario"}
          ,{id:2, value: "leve", label: "  Leve  "}
          ,{id:3, value: "moderado", label: "Moderado"}
          ,{id:4, value: "intenso", label: "Intenso"}
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
      exerciceClick(){
        
        var inpts = document.getElementsByName("option3");
        var chkds =[];
        inpts.forEach(elem => {
          if(elem.checked){
            chkds.push(elem.value)
          }
        });
        //console.log('exerc');
        //console.log(chkds);
        return chkds;
      }

    } 
  }
</script>
<style>
</style>
