<template>
  <div class="food-detail">
    <Navbar />
    <div class="container">
      <!-- breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-success">Beranda</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/hidangan" class="text-success"
                  >Hidangan</router-link
                >
              </li>
              <li class="breadcrumb-item active" aria-current="page">
                Pesanan
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col md-6">
          <img
            :src="'../assets/images/' + product.gambar"
            alt=""
            class="img-fluid shadow"
          />
        </div>
        <div class="col md-6">
          <h2>
            <strong>{{ product.nama }}</strong>
          </h2>
          <hr />
          <h4>
            Harga: <strong>{{ product.harga }}</strong>
          </h4>
          <form v-on:submit.prevent class="mt-4">
            <div class="form-group">
              <label for="jumlah-pesanan">Jumlah Pesanan</label>
              <input
                type="number"
                class="form-control"
                v-model="pesan.jumlah_pemesanan"
              />
            </div>
            <div class="form-group">
              <label for="catatan">Catatan</label>
              <textarea
                v-model="pesan.catatan"
                class="form-control"
                placeholder="pedas, manis, banyakin porsi dan lainnya"
                rows="3"
              ></textarea>
            </div>
            <button @click="pemesanan" type="submit" class="btn btn-success">
              <b-icon-cart-fill></b-icon-cart-fill>Pesan
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "HidanganDetail",
  components: {
    Navbar,
  },

  data() {
    return {
      product: {},
      pesan: {},
    };
  },

  methods: {
    setProduct(data) {
      this.product = data;
    },
    pemesanan() {
      if (this.pesan.jumlah_pemesanan) {
        this.pesan.products = this.product;
        axios
          .post("https://apimakanan.herokuapp.com/keranjangs", this.pesan)
          .then(() => {
            this.$router.push({ path: "/keranjang" });
            alert("Sukses Masuk Keranjang");
          })
          .catch((err) => console.log(err.message));
      } else {
        alert("Jumlah Pesanan Tidak Boleh Kosong");
      }
    },
  },

  mounted() {
    axios
      .get("https://apimakanan.herokuapp.com/products/" + this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>