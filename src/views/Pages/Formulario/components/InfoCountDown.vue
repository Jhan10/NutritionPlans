<template>
<div class="loadingDiv">
  <div name="alertCountDown" v-show="alertCountDown">
  <b-alert
      :show="dismissCountDown"
      dismissible
      :variant="cdVariant"
      @dismissed="dismissCountDown=0"
      @dismiss-count-down="countDownChanged"
    >
    <div name="counting" v-show="loadingCountingVisible">
      <p>{{textBefore}} {{ dismissCountDown }} segundos...</p>
    </div>
    <div name="noCounting" v-show="loadingNoCountingVisible">
      <p>{{ noCountingText }}</p>
    </div>
      <b-progress
        variant="success"
        :max="dismissSecs"
        :value="dismissCountDown"
        height="4px"
      ></b-progress>
    </b-alert>
    
    <!--<b-button @click="showAlert" variant="info" class="m-1"></b-button>-->
  </div>
  <div name="alertStatic" v-show="alertStatic">
    <b-alert
      :variant="stVariant"
      dismissible
      fade
      :show="showDismissibleAlert"
      @dismissed="showDismissibleAlert=false"
    >
      {{stContent}}
    </b-alert>

  </div>

</div>
</template>
<script>

  export default {
    data() {
      return {
        dismissSecs: 22,
        dismissCountDown: 0,
        loadingCountingVisible: true,
        loadingNoCountingVisible: false,
        noCountingText: "no counting text",
        textBefore: "Esse alert vai se fechar em ",
        cdVariant: "warning",
        alertCountDown: false,
        alertStatic: false,
        showDismissibleAlert: false,
        stVariant: "dark",
        stContent: "Conteudo do alerta estático"
      }
    },
    name: 'info-count-down',
    props: {
      type: {
        type: String,
        default: 'default',
        description: 'Alert type'
      },
      dismissible: {
        type: Boolean,
        default: true,
        description: 'Whether alert is dismissible (closeable)'
      },
      icon: {
        type: String,
        default: 'ni ni-atom',
        description: 'Alert icon to display'
      }
    },
       methods: {
      countDownChanged(dismissCountDown) {
        this.dismissCountDown = dismissCountDown
      },
      showAlert() {
        this.dismissCountDown = this.dismissSecs
      },
      defineAlert(before,segs,after) {
        this.dismissCountDown = secs
        this.showDismissibleAlert = true;
      },
      noCountingWarn(message, segs, type){
        this.noCountingText = message;
        this.cdVariant = type || "dark";
        this.dismissCountDown = segs;

        this.alertStatic = false;
        this.alertCountDown = true;

        this.loadingCountingVisible=false;
        this.loadingNoCountingVisible = true;
      },
      countingWarn(before, segs, type){
        this.textBefore = before;
        this.cdVariant = type || "dark";
        this.dismissCountDown = segs;

        this.alertStatic = false;
        this.alertCountDown = true;

        this.loadingNoCountingVisible = false;
        this.loadingCountingVisible =  true;
        
      },
      staticWarn(message, type){
        this.stContent = message;
        this.stVariant = type || "light";

        this.alertCountDown=false;
        this.alertStatic = true;

        this.showDismissibleAlert = true; 
      },
      disposeWarns(){
        this.showDismissibleAlert = false;
        this.dismissCountDown = 0;

        this.alertCountDown=false;
        this.alertStatic = false;
      }
    },
    directives: {
  focus: {
    // definição da diretiva
    inserted: function (el) {
      el.focus()
    }
  }
}
  };
</script>
