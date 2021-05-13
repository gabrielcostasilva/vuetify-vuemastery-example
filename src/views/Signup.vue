<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form>
          <v-text-field
            type="email"
            label="Email"
            v-model="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-autocomplete
            label="Which browser do you use?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input label="Attach profile picture"></v-file-input>
          <v-text-field
            label="Birthday"
            v-model="birthday"
            readonly
          ></v-text-field>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-checkbox
            v-model="agreeToTerms"
            label="Agree to terms & conditions"
            :rules="agreeToTermRules"
            required
          ></v-checkbox>
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      browsers: ['Chrome', 'Safari', 'Firefox'],
      birthday: '',
      agreeToTerms: false,
      email: '',
      nameRules: [
        (value) => !!value || 'Name is required',
        (value) => value.length > 1 || 'Minimum length is 3',
      ],
      agreeToTermRules: [
        (value) => !!value || 'You must agree to signup for an account.',
      ],
      emailRules: [
        (value) => !!value || 'Email is required',
        (value) => value.indexOf('@') !== 0 || 'Email should have a username',
        (value) => value.includes('@') || 'Email should have @ symbol',
        (value) =>
          value.indefOf('.') - value.indexOf('@') > 1 ||
          'Email should contain a valid domain.',
      ],
    }
  },
}
</script>

<style>
</style>