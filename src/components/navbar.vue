<template>
<div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/">
          <img src="../assets/icon.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
          PokeVite
        </router-link>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav">
            <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
            <router-link class="nav-link" to="/about">About</router-link>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

