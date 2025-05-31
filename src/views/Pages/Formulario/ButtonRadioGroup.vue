<template>
  <div class="user-diet-form-gi" data-toggle="buttons">
    <label v-for="(option, index) in options"
           :key="index"
           class="form-control-label"
           :class="[{ active: value === option.value }, buttonClasses]">
           
      <input :value="option.value" v-model="model" type="radio" name="option1" autocomplete="off" checked="false" class="form-control">
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
          {id:1, value: "perderpeso", label: "Perder peso"}
          ,{id:2, value: "manterpeso", label: "Manter peso"}
          ,{id:3, value: "ganharmassa", label: "Ganhar massa"}
          ,{id:4, value: "outro", label: "Outros"}
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
      dietaClick(){
        var inpts = document.getElementsByName("option1");

        var chkds =[];
        inpts.forEach(elem => {
          if(elem.checked){
            chkds.push(elem.value)
          }
        });
        console.log('dieta');
        console.log(chkds);
        return chkds;
      }
    } 
  }
</script>
<style>
</style>
