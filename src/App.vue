
  <template>
  <div>
    <h1>Lista de Recibos</h1>
    <table className="table table-bordered">
      <thead>
        <tr>
          <th>ID</th>
          <th>descripcion</th>
          <th>Monto</th>
          <th>Titulo</th>
          <th>Direccion</th>
          <th>Nombres</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td>{{ product.id }}</td>
          <td>{{ product.descripcion }}</td>
          <td>{{ product.monto }}</td>
          <td>{{ product.titulo }}</td>
          <td>{{ product.direccion }}</td>
          <td>{{product.nombres}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
import "bootstrap/dist/css/bootstrap.css";

export default {
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    axios
      .get("https://localhost:7035/api/productos")
      .then((response) => {
        this.products = response.data;
      })
      .catch((error) => {
        console.error(error);
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
