<template>
  <div class="container-fluid text-center mt-3">
    <router-link v-if="isActivated && isNetworkSupported" to="/profile">Profile</router-link>
    
    <span v-if="isActivated && isNetworkSupported"> | </span>

    <!--<router-link to="/about">About</router-link><span> | </span>-->

    <router-link v-if="isUserMinterAdmin || isUserRoyaltyFeeUpdater || isUserTldAdmin" to="/admin">Admin</router-link>
    <span v-if="isUserMinterAdmin || isUserRoyaltyFeeUpdater || isUserTldAdmin"> | </span>

    <a target="_blank" href="https://situs.ac/">Situs Protocol</a>
    
  </div>

  <div class="container-fluid text-center">
    <!-- GitHub icon (already using Bootstrap icons) -->
    <a class="icons" target="_blank" href="https://github.com/basin-global/Situs-Protocol-Contracts">
        <i class="bi bi-github"></i>
    </a>

    <!-- Warpcast custom icon -->
    <a class="icons" target="_blank" href="https://warpcast.com/~/channel/situs">
        <img src="../assets/icons/warpcast-icon.png" alt="Warpcast" style="width: 24px; height: 24px;"> <!-- Adjust the path and size as needed -->
    </a>

    <!-- Rarible custom icon -->
    <a class="icons" target="_blank" href="https://rarible.com/collection/base/0xd93f89217fcf5f51414e90f62cfe7eeb549a13bc/items">
        <img src="../assets/icons/rarible-icon.png" alt="Rarible" style="width: 24px; height: 24px;"> <!-- Adjust the path and size as needed -->
    </a>

    <!-- OpenSea custom icon -->
    <a class="icons" target="_blank" href="https://opensea.io/assets/base/0xd93f89217fcf5f51414e90f62cfe7eeb549a13bc">
        <img src="../assets/icons/opensea-icon.png" alt="OpenSea" style="width: 24px; height: 24px;"> <!-- Adjust the path and size as needed -->
    </a>
</div>
</template>

<script>
import { useEthers } from 'vue-dapp';
import { mapGetters } from 'vuex';

export default {
  name: "Footer",

  computed: {
    ...mapGetters("network", ["isNetworkSupported"]),
    ...mapGetters("user", ["isUserMinterAdmin", "isUserTldAdmin", "isUserRoyaltyFeeUpdater"]),
    
  },

  setup() {
    const { isActivated } = useEthers()
    return { isActivated }
  },
}
</script>

<style scoped>
a {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

.container-fluid {
  /*background-color: #24263A;*/
  background-color: transparent;
  padding: 20px 0px;
  border-radius: 10px;
}

.icons {
  margin-left: 15px;
  margin-right: 15px;
  font-size: 2em;
}

.polygon {
  vertical-align: text-bottom;
  width: 40px;
}

.polygon svg circle {
  fill: #DBDFEA;
}

.polygon:hover svg circle {
  fill: white;
}
</style>
