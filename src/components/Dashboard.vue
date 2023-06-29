  <template>
  <div>
    <form @submit="submitForm">
      <div class="mb-3">
        <label for="descripcion" class="form-label">Descripcion</label>
        <input
          type="text"
          id="descripcion"
          class="form-control"
          v-model="form.descripcion"
        />
      </div>
      <div class="mb-3">
        <label for="monto" class="form-label">Monto</label>
        <input
          type="monto"
          id="monto"
          class="form-control"
          v-model="form.monto"
        />
      </div>
      <div class="mb-3">
        <label for="titulo" class="form-label">Titulo</label>
        <input
          type="text"
          id="titulo"
          class="form-control"
          v-model="form.titulo"
        />
      </div>
      <div class="mb-3">
        <label for="direccion" class="form-label">Direccion</label>
        <input
          type="text"
          id="direccion"
          class="form-control"
          v-model="form.direccion"
        />
      </div>
<div class="mb-3">
        <label for="nombres" class="form-label">Nombres</label>
        <input
          type="text"
          id="nombres"
          class="form-control"
          v-model="form.nombres"
        />
      </div>
      <button type="submit" class="btn btn-primary">Enviar</button>
    </form>
  </div>
</template>

  <script>
  /* eslint-disable */
import axios from "axios";
import "bootstrap/dist/css/bootstrap.css";

export default {
  name: 'Dashboard',
  data() {
    return {
      showForm: false,
      form: {
        descripcion: "",
        monto: "",
        titulo: "",
        direccion: "",
        nombres:""
      },
    };
  },
  methods: {
    showPopup() {
      this.showForm = true;
    },
    closePopup() {
      this.showForm = false;
    },
    submitForm(event) {
      event.preventDefault();
      axios
        .post("https://localhost:7035/api/productos", this.form)
        .then((response) => {
          console.log(response.data);
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

