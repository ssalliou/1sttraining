<template>
  <b-container fluid="lg">
    <div class="col-6">
      <div class="mt-3">
        <h1 class="text-white bg-dark">Vos collaborateurs</h1>
      </div>

      <div class="mt-3">
        <div v-if="submittedNames.length === 0">
          <h2 class="text-white bg-secondary">Société : xxy</h2>
        </div>
        <ul v-else class="mb-2 pl-0 mt-1">
          <li
            class="d-flex justify-content-between border mb-2"
            v-for="name in submittedNames"
          >
            {{ name }} {{ firstName
            }}<b-icon
              class="d-flex justify-content-between m-2"
              icon="arrow-right"
              scale="1"
              variant="dark"
            ></b-icon>
          </li>
        </ul>
      </div>

      <b-modal
        id="modal-prevent-closing"
        ref="modal"
        title="Ajouter un collaborateur"
        size="lg"
        ok-only
        body-bg-variant="secondary"
        header-bg-variant="dark"
        footer-bg-variant="dark"
        body-text-variant="white"
        header-text-variant="white"
        ok-title="Enregistrer"
        ok-variant="success"
        @show="resetModal"
        @hidden="resetModal"
        @ok="handleOk"
      >
        <form ref="form" @submit.stop.prevent="handleSubmit">
          <!-- Nom !-->

          <b-form-group
            label-for="name-input"
            invalid-feedback="Name is required"
            :state="nameState"
          >
            <b-form-input
              id="name-input"
              placeholder="Nom"
              v-model="name"
              :state="nameState"
              required
            ></b-form-input>

            <!-- Prénom !-->

            <b-form-input
              id="Firstname-input"
              placeholder="Prénom"
              v-model="firstName"
              :state="firstNameState"
              required
              class="mt-3"
            ></b-form-input>

            <!-- Email !-->
            <b-form-input
              id="Email-input"
              v-model="email"
              type="email"
              placeholder="Adresse mail"
              class="mt-3"
              required
            ></b-form-input>

            <!-- Sexe !-->
            <div>
              <b-form-input
                list="sexe"
                placeholder="Sexe"
                class="mt-3"
              ></b-form-input>

              <datalist id="sexe">
                <option v-for="sexe in sexes">{{ sexe }}</option>
              </datalist>
            </div>

            <!-- Fonction !-->

            <b-form-input placeholder="Fonction" class="mt-3"></b-form-input>

            <!-- Contrat !-->
            <div>
              <b-form-input
                list="contrat"
                placeholder="Contrat"
                class="mt-3"
              ></b-form-input>

              <datalist id="contrat">
                <option v-for="contrat in contrats">{{ contrat }}</option>
              </datalist>
            </div>

            <!-- Période essai !-->
            <b-container class="bv-example-row mt-3">
              <b-row>
                <b-col cols="4">
                  <div>Date d'embauche</div>
                  <div>
                    <b-form-input id="date" type="date"></b-form-input>
                  </div>
                </b-col>

                <b-col cols="4">
                  <div>
                    <b-form-group
                      id="essai"
                      label="Durée période d'essai"
                      label-for="essai"
                    >
                      <b-form-input id="text" type="number"></b-form-input>
                      <b-form-select
                        id="essai"
                        v-model="essai"
                        :options="essais"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                </b-col>

                <b-col cols="4">
                  <div>Date fin de contrat</div>
                  <div>
                    <b-form-input id="date" type="date"></b-form-input>
                  </div>
                </b-col>
              </b-row>
            </b-container>
          </b-form-group>
        </form>
      </b-modal>

      <b-button
        v-b-modal.modal-prevent-closing
        block
        variant="success"
        class="d-flex justify-content-between border"
        >Ajouter un nouveau collaborateur<b-icon
          class="d-flex justify-content-between m-2"
          icon="plus-circle"
          scale="1"
          variant="dark"
        ></b-icon
      ></b-button>
    </div>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      nameState: null,
      firstName: "",
      firstNameState: null,
      email: "",
      submittedNames: [],
      sexes: ["F", "M", "Non renseigné"],
      //job: "",
      //jobState: null,
      contrats: ["CDI", "CDD", "Contrat apprentissage", "Contrat prof"],
      essai: null,
      essais: [
        { text: "Choisir jours ou mois", value: null },
        "jour(s)",
        "mois"
      ],
      show: true
    };
  },
  methods: {
    checkFormValidity() {
      const valid = this.$refs.form.checkValidity();
      this.nameState = valid;
      return valid;
    },
    resetModal() {
      this.name = "";
      this.nameState = null;
    },
    handleOk(bvModalEvt) {
      // Prevent modal from closing
      bvModalEvt.preventDefault();
      // Trigger submit handler
      this.handleSubmit();
    },
    handleSubmit() {
      // Exit when the form isn't valid
      if (!this.checkFormValidity()) {
        return;
      }
      // Push the name to submitted names
      this.submittedNames.push(this.name + " " + this.firstName);
      // Hide the modal manually
      this.$nextTick(() => {
        this.$bvModal.hide("modal-prevent-closing");
      });
    }
  }
};
</script>
