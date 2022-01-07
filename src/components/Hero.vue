<template>
  <div class="hero">
    <!-- Desktop -->
    <div class="d-none d-md-block">
      <div class="row mt-4">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Solusi Kenyang Murah,</strong><br />
                ya di MakanYuk
              </h2>
              <p>Ayo, segera order hidangan yang anda inginkan</p>
              <router-link class="btn btn-lg btn-success" to="/hidangan">
                Order
                <b-icon-caret-right-fill></b-icon-caret-right-fill>
              </router-link>
            </div>
          </div>
        </div>
        <div class="col">
          <img src="../assets/images/Hero.png" width="100%" alt="" />
        </div>
      </div>
    </div>

    <!-- Mobile -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-4">
        <div class="col-md-6">
          <img src="../assets/images/Hero.png" width="100%" alt="" />
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Solusi Kenyang Murah,</strong><br />
                ya di MakanYuk
              </h2>
              <p>Ayo, segera order hidangan yang anda inginkan</p>
              <a class="btn btn-lg btn-success" href="">
                Order
                <b-icon-caret-right-fill></b-icon-caret-right-fill>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
};
</script>

<style></style>
