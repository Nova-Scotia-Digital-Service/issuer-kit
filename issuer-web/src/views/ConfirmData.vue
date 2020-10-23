<style scoped lang="scss">
// .claim-name {
//   font-style: italic;
// }
//CNS style
.btnText {
  color: #eeeeee;
}
.claim-value {
  font-weight: bold;
}
</style>

<template>
  <v-container fluid>
    <v-card class="mx-auto my-2 lighten-4" max-width="800" tile>
      <v-card-title class="headline mb-1">Review and Confirm</v-card-title>

      <v-list disabled>
        <v-list-item-group color="primary">
          <v-list-item v-for="(item, i) in claims" :key="i">
            <v-list-item-content>
              <v-list-item-title>
                <v-row align="center" justify="space-around">
                  <v-col cols="4">
                    <v-text class="mx-3 claim-name">{{ item.name }}</v-text>
                  </v-col>
                  <v-col cols="2">
                    <v-icon small class="mx-3">fas fa-arrow-right</v-icon>
                  </v-col>
                  <v-col cols="4">
                    <span class="mx-3 claim-value">{{ item.value }}</span>
                  </v-col>
                </v-row>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>

      <v-divider class="mx-4"></v-divider>

      <v-container fluid>
        <v-row align="center" justify="space-around">
          <v-col cols="1"></v-col>
          <v-col cols="10">
            <v-checkbox
              v-model="confirmed"
              label="I confirm that the above information is correct, and that I want to proceed."
            ></v-checkbox>
          </v-col>
          <v-col cols="1"></v-col>
        </v-row>
        <v-row align="center" justify="space-between" class="mr-2">
          <v-col cols="6" md="2">
            <a color="error" href="{ path: 'credential-data' }" class="underLineLink">Back</a>
          </v-col>
          <v-col cols="6" md="2">
            <v-btn
              raised large          
              color="btnSuccess"
              class="btnText"
              :disabled="!confirmed"
              :to="{ path: 'connect' }"
              >Proceed</v-btn
            >
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Claim } from "../models/credential";

@Component
export default class ConfirmData extends Vue {
  private claims!: Array<Claim>;
  private confirmed = false;

  created() {
    const credential = this.$store.getters["credential/getCredential"];
    this.claims = credential.claims;
  }
}
</script>
