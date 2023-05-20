<template>
  <v-card 
    class="mx-auto px-6 py-8" 
    max-width="344"
    title="Admin Login">
    <v-container>
      <v-form
        v-model="form"
        @submit.prevent="onSubmit"
    >
        <v-text-field
        v-model="email"
        color="primary"
        :readonly="loading"
        :rules="[required]"
        class="mb-2"
        clearable
        label="Email"
        variant="underlined"
        ></v-text-field>

        <v-text-field
        v-model="password"
        color="primary"
        :readonly="loading"
        :rules="[required]"
        clearable
        label="Password"
        placeholder="Enter your password"
        variant="underlined"
        ></v-text-field>

        <br>

        <v-btn
        :disabled="!form"
        :loading="loading"
        block
        color="success"
        size="large"
        type="submit"
        variant="elevated"
        >
        Sign In
        </v-btn>
      </v-form>
    </v-container>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      form: false,
      email: null,
      password: null,
      loading: false,
    }),

    methods: {
      onSubmit () {
        if (!this.form) return

        this.loading = true

        setTimeout(() => (this.loading = false), 2000)
      },
      required (v) {
        return !!v || 'Field is required'
      },
    },
  }
</script>