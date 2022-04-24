<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar navbar-dark bg-primary">
      <div class="container-fluid">
        <h3>
          <RouterLink class="nav-brand nav-link btn btn-primary text-white" to="/">Test Blog</RouterLink>
        </h3>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav" v-if="auth.authentified">
            <li class="nav-item">
              <h2>
                <RouterLink class="nav-link" to="/profil">Profile</RouterLink>
              </h2>
            </li>
          </ul>
          <ul class="navbar-nav d-flex ms-auto" v-if="auth.authentified">
            <li class="nav-item ms-lg-3">
              <button class="btn btn-danger" v-on:click="setAuth(null, false)">
                <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-door-open-fill" viewBox="0 0 16 16" >
                  <path d="M1.5 15a.5.5 0 0 0 0 1h13a.5.5 0 0 0 0-1H13V2.5A1.5 1.5 0 0 0 11.5 1H11V.5a.5.5 0 0 0-.57-.495l-7 1A.5.5 0 0 0 3 1.5V15H1.5zM11 2h.5a.5.5 0 0 1 .5.5V15h-1V2zm-2.5 8c-.276 0-.5-.448-.5-1s.224-1 .5-1 .5.448.5 1-.224 1-.5 1z" />
                </svg>
              </button>
            </li>
          </ul>
          <ul class="navbar-nav d-flex ms-auto" v-else>
            <li class="nav-item">
              <RouterLink
                class="nav-link btn btn-primary text-white"
                to="/login"
                >Se connecter</RouterLink
              >
            </li>
            <li class="nav-item ms-lg-3">
              <RouterLink
                class="nav-link btn btn-warning text-white"
                to="/register"
                >S'enregistrer</RouterLink
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import { RouterLink } from "vue-router";

export default {
  props: ["auth", "setAuth"],
  setup(props, context) {}
};
</script>
