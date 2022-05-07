<template>
  <!-- Sidebar -->
  <div class="sidebar sidebar-style-2">
    <div class="sidebar-wrapper scrollbar scrollbar-inner">
      <div class="sidebar-content">
        <div class="user">
          <div class="avatar-sm float-left mr-2">
            <img src="assets/img/profile.jpg" alt="..." class="avatar-img rounded-circle">
          </div>
          <div class="info">
            <a data-toggle="collapse" href="" aria-expanded="true">
								<span>
									Gözde Bayru
								</span>
            </a>
            <div class="clearfix"></div>
          </div>
        </div>
        <ul class="nav nav-primary">

          <router-link
              active-class="active"
              to="/dashboard"
              tag="li"
              class="nav-item">
            <a>
              <i class="fas fa-home"></i>
              <p>Dashboard</p>
            </a>
          </router-link>


          <li class="nav-section">
							<span class="sidebar-mini-icon">
								<i class="fa fa-ellipsis-h"></i>
							</span>
            <h4 class="text-section">General</h4>
          </li>


          <router-link
              v-if="rights.category"
              active-class="active"
              to="/category"
              tag="li"
              class="nav-item">
            <a>
              <i class="fab fa-stack-overflow"></i>
              <p>Kategoriler</p>
            </a>
          </router-link>

          <router-link
              v-if="rights.traveller"
              active-class="active"
              to="/traveller"
              tag="li"
              class="nav-item">
            <a>
              <i class="fas fa-utensils"></i>
              <p>Tatiller</p>
            </a>
          </router-link>


          <router-link
              v-if="rights.users"
              active-class="active"
              to="/users"
              tag="li"
              class="nav-item">
            <a>
              <i class="fas fa-user-ninja"></i>
              <p>Kullanıcılar</p>
            </a>
          </router-link>

          <router-link
              v-if="rights.settings"
              active-class="active"
              to="/settings"
              tag="li"
              class="nav-item">
            <a>
              <i class="flaticon-settings"></i>
              <p>Ayarlar</p>
            </a>
          </router-link>


        </ul>
      </div>
    </div>
  </div>
  <!-- End Sidebar -->
</template>
<script>


import {mapGetters} from "vuex";

export default {
  data() {
    return {
      user: {},
      rights: {}
    }
  },
  created() {
    this.user = this.getUser
    this.rights = this.getUser.rights
  },
  computed: {
    ...mapGetters(["getUser"]),
  },
}
</script>
