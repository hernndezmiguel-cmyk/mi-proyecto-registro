<template>
  <div class="formulario-container">
    <h2>Formulario de Registro de Usuarios</h2>
    <form @submit.prevent="handleSubmit" class="formulario">
      <div class="form-group">
        <label for="nombre">Nombre Completo:</label>
        <input
          type="text"
          id="nombre"
          v-model="formData.nombre"
          placeholder="Ingrese su nombre completo"
          required
        />
      </div>

      <div class="form-group">
        <label for="direccion">Dirección:</label>
        <input
          type="text"
          id="direccion"
          v-model="formData.direccion"
          placeholder="Ingrese su dirección"
          required
        />
      </div>

      <div class="form-group">
        <label for="edad">Edad:</label>
        <input
          type="number"
          id="edad"
          v-model.number="formData.edad"
          placeholder="Ingrese su edad"
          min="18"
          max="120"
          required
        />
      </div>

      <button type="submit" class="btn-submit">Registrar Usuario</button>
    </form>

    <div v-if="mensaje" class="mensaje" :class="tipoMensaje">
      {{ mensaje }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormularioRegistro',
  data() {
    return {
      formData: {
        nombre: '',
        direccion: '',
        edad: null
      },
      mensaje: '',
      tipoMensaje: ''
    }
  },
  methods: {
    handleSubmit() {
      if (this.formData.edad < 18) {
        this.mensaje = 'Debe ser mayor de 18 años';
        this.tipoMensaje = 'error';
        return;
      }

      this.mensaje = `Usuario ${this.formData.nombre} registrado correctamente`;
      this.tipoMensaje = 'exito';
      
      setTimeout(() => {
        this.formData = { nombre: '', direccion: '', edad: null };
        this.mensaje = '';
      }, 3000);
    }
  }
}
</script>

<style scoped>
.formulario-container {
  max-width: 500px;
  margin: 50px auto;
  padding: 30px;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

h2 {
  text-align: center;
  color: #42b983;
  margin-bottom: 30px;
}

.formulario {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 8px;
  font-weight: bold;
  color: #333;
}

input {
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  transition: border-color 0.3s;
}

input:focus {
  outline: none;
  border-color: #42b983;
}

.btn-submit {
  padding: 12px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn-submit:hover {
  background-color: #369970;
}

.mensaje {
  margin-top: 20px;
  padding: 12px;
  border-radius: 4px;
  text-align: center;
  font-weight: bold;
}

.exito {
  background-color: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.error {
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}
</style>