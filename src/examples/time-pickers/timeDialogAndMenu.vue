<template>
  <v-layout row wrap>
    <v-flex xs11 sm5>
      <v-menu
        ref="menu"
        :close-on-content-click="false"
        v-model="menu2"
        :nudge-right="40"
        :return-value.sync="time"
        lazy
        transition="scale-transition"
        offset-y
        full-width
        max-width="290px"
        min-width="290px"
      >
        <v-text-field
          slot="activator"
          v-model="time"
          label="Picker in menu"
          prepend-icon="access_time"
          readonly
        ></v-text-field>
        <v-time-picker
          v-if="menu2"
          v-model="time"
          full-width
          @change="$refs.menu.save(time)"
        ></v-time-picker>
      </v-menu>
    </v-flex>
    <v-spacer></v-spacer>
    <v-flex xs11 sm5>
      <v-dialog
        ref="dialog"
        v-model="modal2"
        :return-value.sync="time"
        persistent
        lazy
        full-width
        width="290px"
      >
        <v-text-field
          slot="activator"
          v-model="time"
          label="Picker in dialog"
          prepend-icon="access_time"
          readonly
        ></v-text-field>
        <v-time-picker
          v-if="modal2"
          v-model="time"
          full-width
        >
          <v-spacer></v-spacer>
          <v-btn flat color="primary" @click="modal2 = false">Cancel</v-btn>
          <v-btn flat color="primary" @click="$refs.dialog.save(time)">OK</v-btn>
        </v-time-picker>
      </v-dialog>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        time: null,
        menu2: false,
        modal2: false
      }
    }
  }
</script>
