<template>
  <div class="border-top border-dark mt-5">
    <footer class="container py-5">
      <div class="row">
        <div class="col-12 col-md">
          <small class="d-block mb-3 text-muted"><b-icon icon="house-fill" scale="1.25" shift-v="1.25" aria-hidden="true"></b-icon> Sylvain © 2021</small>
        </div>
        <div class="col-6 col-md">
          <h5>Portefeuille</h5>
          <ul class="list-unstyled text-small">
            <li><a class="text-muted" href="#">Société A</a></li>
            <li><a class="text-muted" href="#">Société B</a></li>
          </ul>
        </div>
        <div class="col-6 col-md">
          <h5>Organismes</h5>
          <ul class="list-unstyled text-small">
            <li><a class="text-muted" href="#">URSSAF</a></li>
            <li><a class="text-muted" href="#">Pôle Emploi</a></li>
            <li><a class="text-muted" href="#">Retraite complémentaire</a></li>
            <li><a class="text-muted" href="#">Prévoyance</a></li>
            <li><a class="text-muted" href="#">Mutuelle</a></li>
          </ul>
        </div>
        <div class="col-6 col-md">
          <h5>Déclarations</h5>
          <ul class="list-unstyled text-small">
            <li><a class="text-muted" href="#">DSN mensuelle</a></li>
            <li><a class="text-muted" href="#">Bordereaux annuels</a></li>
          </ul>
        </div>
        <div class="col-6 col-md">
          <h5>Contacts</h5>
          <ul class="list-unstyled text-small">
            <li><a class="text-muted" href="#">Mail </a></li>
            <li><a class="text-muted" href="#">Zoom </a></li>
          </ul>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Footer"
};
</script>
