<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary fixed-top">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">BILYURL.COM</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Features</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Pricing</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <div class="main-container">
   
  </div>
</template>

<style>
/* Réinitialisation du style de base */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* S'assure que le conteneur prend tout l'espace de l'écran */
body,
html {
  width: 100%;
  height: 100%;
  overflow: hidden; /* Pour éviter tout défilement */
  background-color: #f1f1f1; /* Couleur de fond pour le contenu principal */
}

/* Barre de navigation fixée en haut */
.navbar {
  z-index: 1;
  height: 70px; /* Hauteur de la barre de navigation */
}

/* Conteneur principal remplit l'espace restant */
.main-container {
  display: flex;
  flex-direction: column; /* Pour empiler les éléments verticalement */
  width: 100vw; /* Prend toute la largeur de la vue */
  height: calc(
    100vh - 70px
  ); /* Utilise toute la hauteur de la vue moins la hauteur de la navbar */
  margin-top: 70px; /* Décalage sous la barre de navigation */
  overflow: hidden; /* Évite le défilement */
}
</style>
