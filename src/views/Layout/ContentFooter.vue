<template>
  <footer class="footer px-4">
    <b-row align-v="center" class="justify-content-lg-between">
      <b-col lg="6">
        <div class="copyright text-center text-lg-left text-muted">
          © {{year}} <a href="#" class="font-weight-bold ml-1" target="_blank">Berry Company's</a>
        </div>
      </b-col>
      <b-col lg="6">
        <b-nav align="center" class="nav-footer justify-content-lg-end">
          <b-nav-item href="#"  target="_blank">
             Empresa
          </b-nav-item>
          <b-nav-item href="#" target="_blank">
           Sobre nós
          </b-nav-item>
          <b-nav-item href="#" target="_blank">
            Blog
          </b-nav-item>
          <b-nav-item href="#" target="_blank">
            Licença
          </b-nav-item>
        </b-nav>
      </b-col>
    </b-row>
  </footer>
</template>
<script>
export default {
  data() {
    return {
      year: new Date().getFullYear()
    };
  }
};
</script>
<style></style>
