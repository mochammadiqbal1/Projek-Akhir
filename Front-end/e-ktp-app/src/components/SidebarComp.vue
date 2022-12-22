<template>
  <div>
    <div class="side">
      <div class="sidebar d-flex flex-column">
        <div>
          <h1 class="e-ktp d-flex justify-content-center">
            <p class="pt-2">E-KTP</p>
          </h1>
        </div>
        <hr />

        <div class="menu">
          <router-link to="/home" class="nav-link">
            <div>
              <h6 class="text-white home d-flex">
                <p class="pt-2">Home</p>
              </h6>
            </div>
          </router-link>

          <router-link to="/addkk" class="nav-link">
            <div>
              <h6 class="text-white tambah-kk d-flex">
                <p class="pt-2">Tambah KK</p>
              </h6>
            </div>
          </router-link>

        </div>

        <div class="s">
          <router-link to="/" class="nav-link">
            <h5 class="text-white d-flex">
              
              <p class="pt-1" >Logout</p>
              
            </h5>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SidebarS",
};
</script>

<!-- CSS -->
<style scoped>
span {
  margin-right: 10px;
  padding-bottom: 5px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.sidebar {
  width: 250px;
  height: 100vh;
  background-color: #EB455F;
  box-shadow: 0 4px 15px 0 rgba(66, 67, 67, 0.436);
  /* background-color: rgb(39, 201, 63); */

  /* background-color: rgb(255, 189, 46); */

  /* background-color: rgb(255, 95, 86); */
  /* border-radius: 25px; */
  /* margin-top: 25px; */
  /* margin-left: 10px; */
  position: fixed;
}

.logout {
  /* margin: auto; */
  margin-bottom: 20px;
}

h1 {
  margin-top: 30px;
  padding-top: 5px;
}

hr {
  background-color: rgb(255, 255, 255);
  padding: 5px;
  margin-top: 15px;
  margin-bottom: 10px;
  border: none;
}

svg {
  width: 50px;
  height: auto;
  margin-right: 10px;
  margin-left: 10px;
}

.menu div {
  margin-left: 20px;
  margin-top: 30px;
}

h5 {
  margin-left: 20px;
  margin-top: 250px;
}

svg {
  width: 30px;
  height: auto;
}

.home {
  padding: 5px 5px;
  border-radius: 10px 0px 0px 10px;
}

.home:hover {
  background-color: #ff7489;
  cursor: pointer;
}

.tambah-kk {
  padding: 5px 5px;
  border-radius: 10px 0px 0px 10px;
}

.tambah-kk:hover {
  background-color: #ff7489;
  cursor: pointer;
}

.daftar-anggota {
  padding: 5px 5px;
  border-radius: 10px 0px 0px 10px;
}

.daftar-anggota:hover {
  background-color: #EB455F;
  cursor: pointer;
}

.router-link-exact-active,
.router-link-active {
  background-color: #EB455F;
  border-radius: 10px 0px 0px 10px;
  cursor: pointer;
}

h4 .text-white mt-auto mb-3:hover {
  background-color: #EB455F;
  padding: 5px 5px 5px 5px;
  border-radius: 10px 0px 0px 10px;
}

div .mt-auto:hover {
  background-color: #EB455F;
  cursor: pointer;
}

/* Material Icon */
.material-symbols-outlined {
  font-weight: 100;
}

#badge {
  font-size: 60px;
}

#home {
  font-size: 40px;
}

#add-card {
  font-size: 40px;
}

#post-id {
  font-size: 40px;
}

#logout {
  font-size: 40px;
}

.e-ktp {
  color: white;
}
</style>