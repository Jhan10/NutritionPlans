<template>
  <div>
    <div class="header pb-8 pt-5 pt-lg-8 d-flex align-items-center profile-header"
        style="min-height: 600px; background-image: url(img/theme/veduras4.jpg); background-size: cover; background-position: center top;">
      <b-container fluid>
        <!-- Mask -->
        <span class="mask bg-gradient-success opacity-3"></span>
        <!-- Header container -->
        <b-container fluid class="d-flex align-items-center">
          <b-row >
            <b-col lg="7" md="10">
              <h1 class="display-2 text-white">Olá Admin</h1>
              <p class="text-white mt-0 mb-5">Preencha o formulário abaixo para receber seu Plano Alimentar Personalizado para Dietas</p>
              <div class="hiddinIniting">
              <a href="#!" class="btn btn-info">Edit profile</a>
              </div>
            </b-col>
          </b-row>
        </b-container>
      </b-container>
    </div>

    <b-container fluid class="mt--6">
      <b-row>
<div class="hiddinIniting">
        <b-col xl="4" class="order-xl-2 mb-5">
          <user-card></user-card>
        </b-col>
</div>
        <b-col xl="8" class="order-xl-1">
          <formulario-form></formulario-form>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
  import FormularioForm from './Formulario/FormularioForm.vue';
  import UserCard from './UserProfile/UserCard.vue';

  export default {
    components: {
      FormularioForm,
      UserCard
    }
  };
</script>
<style>
</style>
