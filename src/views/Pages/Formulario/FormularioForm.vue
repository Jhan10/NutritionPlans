<template>
  <card>
    <b-row align-v="center" slot="header" >
      <b-col cols="8">
        <h3 class="mb-0">Gerar dieta </h3>
      </b-col>
      <b-col cols="4" class="text-right">
        <a href="#!" class="btn btn-sm btn-primary">Configurações</a>
        <button v-if="false" type="button" class="btn btn-sm btn-primary" @click="teste">teste sql</button>
        
      </b-col>
    </b-row>

    <b-form role="form" @submit.prevent="sendForm">
      <h6 class="heading-small text-muted mb-4">Informaçoes basicas</h6>

      <div class="pl-lg-4">
        <b-row>
          <b-col lg="6">
            <base-input
              type="text"
              label="Nome"
              placeholder="Ingrid Santos"
              v-model="user.username"
            >
            </base-input>
          </b-col>
          <b-col lg="6">
            <base-input
              type="email"
              label="Endereço de Email"
              placeholder="ingridsantos@email.com"
              v-model="user.email"
            >
            </base-input>
          </b-col>
        </b-row>
      </div>
      <hr class="my-4">

      <!-- Objetivo -->
      <h6 class="heading-small text-muted mb-4">Objetivo Dieta</h6>
       <b-row>

<div class="hiddinIniting">

         <b-col lg="4" class="user-diet-form-gi">
            <base-input
              type="radio"
              label="Perder peso"
              placeholder="ppeso"
              v-model="user.ppeso"
            ></base-input>
            <base-input
              type="radio"
              label="Manter peso"
              placeholder="mpeso"
              v-model="user.mpeso"
            ></base-input>
            <base-input
              type="radio"
              label="Ganhar massa"
              placeholder="gmassa"
              v-model="user.gmassa"
            ></base-input>
         </b-col>
</div>         
         <b-col lg="7" class="">
           <button-radio-group></button-radio-group>
         </b-col>
          <b-col lg="5">
            <b-form-textarea rows="4" value="" id="outro-form-textaria" 
            v-model="user.outraDieta" placeholder="Outros..."></b-form-textarea>
          </b-col>
       </b-row>
      <hr class="my-4">

      <!-- Medidas -->
      <h6 class="heading-small text-muted mb-4">Medidas | Nivel de exercicios que pratico</h6>

      <div class="pl-lg-4">
        <b-row>
          <b-col lg="2">
            <base-input
              type="text"
              label="Altura"
              placeholder="ex: 1,84 m"
              v-model="user.altura"
            >
            </base-input>
          </b-col>
          <b-col lg="2">
            <base-input
              type="text"
              label="Peso"
              placeholder="ex: 95 Kg"
              v-model="user.peso"
            >
            </base-input>
          </b-col>
          <b-col lg="6" class="">
            <button-radio-group-exercice></button-radio-group-exercice>
          </b-col>
        </b-row>
      </div>

<hr class="my-4">
      <!-- Restrições -->
      <h6 class="heading-small text-muted mb-4">Restrições alimentares</h6>

      <div class="pl-lg-4">
        <b-row>
        <b-col lg="7" class="user-diet-form-chekb">
          <button-checkbox-group>
          </button-checkbox-group>
        </b-col>
        <b-col lg="5">
            <b-form-textarea rows="4" value="" id="outro-form-textaria" 
            v-model="user.outraRestricao" placeholder="Outros..."></b-form-textarea>
          </b-col>
        </b-row>
      </div>
      <hr class="my-4">
      <!-- Description -->
      <h6 class="heading-small text-muted mb-4">Observações</h6>
      <div class="pl-lg-4">
        <b-form-group label="Alimentos específicos | Preferências" label-class="form-control-label" class="mb-0" label-for="about-form-textaria">
         <!--  <label class="form-control-label">About Me</label> -->
          <b-form-textarea rows="4" value="" id="about-form-textaria"
          v-model="user.preferencias" 
          placeholder="Prefiro adoçante ao açucar tradicional, ..."></b-form-textarea>
        </b-form-group>
      </div>

      <hr class="my-4">
      <!-- Description -->
      <h6 class="heading-small text-muted mb-4">Detalhes</h6>
      <br />
      <div class="pl-lg-4">
          <b-row>
            <b-col lg="9" class="">
              <b-form-group label="Orçamento semanal para compra de alimentos" label-class="form-control-label" class="mb-0" 
             label-for="about-form-textaria">
                 <button-radio-group-orcamento></button-radio-group-orcamento>
              </b-form-group>
            </b-col>
          </b-row>
          <br />
      </div>
      <hr class="my-4">
<h6 class="heading-small text-muted mb-4">Refeições</h6>
          <br />
      <div class="pl-lg-3">
          <b-row>
            <b-col lg="12" class="">
               <b-form-group label="Horário para café da manhã" label-class="form-control-label" class="mb-0" label-for="about-form-textaria">
                 <button-radio-group-cafe></button-radio-group-cafe>
               </b-form-group>
            </b-col>
          </b-row>
          <br />
          <b-row>
            <b-col lg="12" class="">
               <b-form-group label="Horário para lanche da manhã" label-class="form-control-label" class="mb-0" label-for="about-form-textaria">
                 <button-radio-group-lanchem></button-radio-group-lanchem>
               </b-form-group>
            </b-col>
          </b-row>
          <br />
          <b-row>
            <b-col lg="12" class="">
               <b-form-group label="Horário para almoço" label-class="form-control-label" class="mb-0" label-for="about-form-textaria">
                 <button-radio-group-almoco></button-radio-group-almoco>
               </b-form-group>
            </b-col>
          </b-row>
          <br />
          <b-row>
            <b-col lg="12" class="">
               <b-form-group label="Horário para lanche da tarde" label-class="form-control-label" class="mb-0" label-for="about-form-textaria">
                 <button-radio-group-lanchet></button-radio-group-lanchet>
               </b-form-group>
            </b-col>
          </b-row>
          <br />
          <b-row>
            <b-col lg="12" class="">
               <b-form-group label="Horário para jantar" label-class="form-control-label" class="mb-0" label-for="about-form-textaria">
                 <button-radio-group-jantar></button-radio-group-jantar>
               </b-form-group>
            </b-col>
          </b-row>

      </div>
      <br /> <br />
      <div>
      <b-row  slot="footer" >
        <b-col cols="12" class="text-right">
          <div class="loading">
            <img alt="loading" src="img/loading.gif" class="loadingImg" v-show="loadingVisible" :style="loadingVisible">
            <input type="submit" :disabled="submitButton.disableButtonLoading" name="formButton" class="btn btn-sm btn-primary submit submitButton" :value="submitButton.textName">
          </div>
        
        
        </b-col>
      </b-row>
      </div>
    </b-form>
  </card>
</template>
<script>
import ButtonRadioGroup from './ButtonRadioGroup.vue';
import BaseRadio from '../../../components/Inputs/BaseRadio.vue';
import ButtonCheckboxGroup from './ButtonCheckboxGroup.vue';
import ButtonRadioGroupExercice from './ButtonRadioGroupExercice.vue';
import ButtonRadioGroupOrcamento from './ButtonRadioGroupOrcamento.vue';
import ButtonRadioGroupCafe from './components/refeicoes/ButtonRadioGroupCafe.vue';
import ButtonRadioGroupLanchem from './components/refeicoes/ButtonRadioGroupLancheM.vue';
import ButtonRadioGroupAlmoco from './components/refeicoes/ButtonRadioGroupAlmoco.vue';
import ButtonRadioGroupLanchet from './components/refeicoes/ButtonRadioGroupLancheT.vue';
import ButtonRadioGroupJantar from './components/refeicoes/ButtonRadioGroupJantar.vue';

export default {
  components: {
    ButtonRadioGroup,
    BaseRadio,
    ButtonCheckboxGroup,
    ButtonRadioGroupExercice,
    ButtonRadioGroupOrcamento,
    ButtonRadioGroupCafe,
    ButtonRadioGroupLanchem,
    ButtonRadioGroupAlmoco,
    ButtonRadioGroupLanchet,
    ButtonRadioGroupJantar,

  },
  data() {
    return {
      user: {
        company: 'Creative Code Inc.',
        username: '',
        email: '',
        firstName: 'Mike',
        lastName: 'Andrew',
        address: 'Bld Mihail Kogalniceanu, nr. 8 Bl 1, Sc 1, Ap 09',
        city: 'New York',
        country: 'USA',
        postalCode: '',
        aboutMe: `Lamborghini Mercy, Your chick she so thirsty, I'm in that two seat Lambo.`
      },
      submitButton:{
        textName: "Enviar plano",
        disableButtonLoading: false,
      },
      loadingVisible: false
    };
  },
  methods: {
    loadingForm(){

      this.submitButton.disableButtonLoading=true;
      this.submitButton.textName="Aguarde...";
      this.loadingVisible=true;
    },
    unload(){
        let btn = document.getElementsByName("formButton")[0];

        btn.removeAttribute("disabled");
        this.submitButton.textName="Enviar plano";
        this.loadingVisible=false;
    },
    retornoGenerate(data){
      console.log(data);
     alert(data);
    },

    async callApi(data){
      let y=[{}];
      const req = await fetch("https://bot-ia-talk-manager.vercel.app/FormSite"
      ,{
        method:'POST'
        ,headers:{'Content-Type': 'application/json'}
      
      ,body: JSON.stringify(data)
      }).then(async (res)=>{

        console.log("req.json()");
         y=await res.json()
        console.log(y);
        
      }).catch((data)=>{
        console.error(data);
        return data;
      });
      
      return y;
  },

  async sendForm(e){
    e.preventDefault();

    this.loadingForm();
    const data = {
      nome: this.user.username,
      email: this.user.email,
      dieta: this.getDiet().toString(),
      altura: this.user.altura,
      peso: this.user.peso,
      nivelExer: this.getNivelExer().toString(),
      restricoes: Array.from(this.getRestritions()),
      preferencias: this.user.preferencias,
      orcamento: this.getOrcamento().toString(),
      cafe: this.getCafe().toString(),
      lanchem: this.getLancheM().toString(),
      almoco: this.getAlmoco().toString(),
      lanchet: this.getLancheT().toString(),
      jantar: this.getJantar().toString(),
    };
    console.log(data);

    const res = await this.callApi(data);
    this.unload();
    console.log(res);

     if(res){
      if(res.sol && res.sol.status){
        this.retornoGenerate(res.sol.status);
      }else{
        this.retornoGenerate("Não foi possivel recuperar o status da solicitação. Contate o Administrador do sistema.")
      }
    }else{
      this.retornoGenerate("Solicitação não processada. Tente novamente ou contate o Administrador do sistema.")
    }

      //console.log("response");
      //console.log(res);
  },

  getDiet(){
    let arr = ButtonRadioGroup.methods.dietaClick();
 
       if(arr !== undefined){
        let oDiet=this.user.outraDieta;
        if(oDiet != undefined){
          return oDiet;
        }
     return arr;
   }
   return null;
  },

  getRestritions(){
    let arr = ButtonCheckboxGroup.methods.boxClick();
    if(arr.length > 0){
      if(arr.includes('outro')){
        arr.splice(arr.indexOf('outro'),1);

        let oRestr=this.user.outraRestricao;
        if(oRestr != undefined){
          arr.push(oRestr);
        }
        
        return arr;
    }
    return arr;
   }
  },
  getNivelExer(){
    let nivelEx = ButtonRadioGroupExercice.methods.exerciceClick();
      if(nivelEx !== undefined){
        return nivelEx;
      }
    return null
   },
   getOrcamento(){
    let orcam = ButtonRadioGroupOrcamento.methods.budgetClick();
    if(orcam !== undefined){
      return orcam;
    }
    return null
   },
   getCafe(){
    let cafe = ButtonRadioGroupCafe.methods.cafeClick();
    if(cafe !== undefined){
      return cafe;
    }
    return null
   },
   getLancheM(){
    let value = ButtonRadioGroupLanchem.methods.lancheMClick();
    if(value !== undefined){
      return value;
    }
    return null
   },
   getAlmoco(){
    let value = ButtonRadioGroupAlmoco.methods.almocoClick();
    if(value !== undefined){
      return value;
    }
    return null
   },
   getLancheT(){
    let value = ButtonRadioGroupLanchet.methods.lancheTClick();
    if(value !== undefined){
      return value;
    }
    return null
   },
   getJantar(){
    let value = ButtonRadioGroupJantar.methods.jantarClick();
    if(value !== undefined){
      return value;
    }
    return null
   },
   async teste(){

    const data = {
      nome: "Duda site002",
      email: "geandinho2010@gmail.com",
      dieta: "perderpeso",
      altura: "1,78",
      peso: 108,
      nivelExer: "sedentario",
      restricoes: [
        "gluten"
    ],
      preferencias: "bolo",
      orcamento: "Até R$150",
      cafe: "nfaz",
      lanchem: "10",
      almoco: "12",
      lanchet: "nfaz",
      jantar: "20",
    };

    console.log(data);


    let y=[{}];
      const req = await fetch("http://bot-ia-talk-manager.vercel.app/teste"
      ,{
        method:'POST'
        ,headers:{'Content-Type': 'application/json'}
      
      ,body: JSON.stringify(data)
      }).then(async (res)=>{

        console.log("req.json()");
         y=await res.json()
        console.log(y);
        
      }).catch((data)=>{
        console.error(data);
      });

    this.unload();
    console.log(final);

     if(res){
      if(res.status){
        this.retornoGenerate(res.status);
   }
  }
}
  },
  mounted(){
  }
};
</script>
<style>
</style>