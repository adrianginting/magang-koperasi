<template>
  <v-card>
    <v-layout>
      <v-navigation-drawer
        v-model="drawer"
        :rail="rail"
        permanent
        @click="rail = false"
      >
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
          title="John Leider"
          nav
        >
          <template v-slot:append>
            <v-btn
              variant="text"
              icon="mdi-chevron-left"
              @click.stop="rail = !rail"
            ></v-btn>
          </template>
        </v-list-item>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item v-for="item in items" :key="item.value" :prepend-icon="item.icon" :title="item.title" @click="goTo(item.route)"></v-list-item>
        </v-list>

        <template v-slot:append>
          <v-list density="compact" nav>
              <v-list-item prepend-icon="mdi-logout" title="Logout" value="logout">
              </v-list-item>
          </v-list>
        </template>
        
      </v-navigation-drawer>
      <v-main >
        <HelloWorld v-if="navigasi == 'Home'"/>
        <TransaksiComponent v-else-if="navigasi == 'Transaksi'"/>
        <ReportComponent v-else-if="navigasi == 'Laporan'"/>
        <MyAccountComponent v-else-if="navigasi == 'Account'"/>
        <UsersComponent v-else-if="navigasi == 'Users'"/>
        <WidgetsComponents v-else-if="navigasi == 'Widgets'"/>

        <HelloWorld v-else/>
      </v-main>
    </v-layout>
  </v-card>
</template>

<script>
import { defineComponent } from 'vue';
import HelloWorld from '../components/HelloWorld.vue';
import TransaksiComponent from '../components/TransaksiComponent.vue';
import ReportComponent from '../components/ReportComponent.vue';
import MyAccountComponent from '../components/MyAccountComponent.vue';
import UsersComponent from '../components/UsersComponent.vue';
import WidgetsComponents from '../components/WidgetsComponents.vue';


export default defineComponent({

name: 'HomeView',

components: {
  HelloWorld,
  MyAccountComponent,
  TransaksiComponent,
  ReportComponent,
  UsersComponent,
  WidgetsComponents,
},
data () {
  return {
  navigasi: '',
  drawer: true,
  items: [
      { icon: "mdi-home", title: "Home", value: "home", route: "Home" },
      { icon: "mdi-receipt", title: "Transaksi", value: "transaksi", route: "Transaksi" },
      { icon: "mdi-file-chart", title: "Laporan", value: "laporan", route: "Laporan" },
      { icon: "mdi-account", title: "My Account", value: "account", route: "Account" },
      { icon: "mdi-account-group-outline", title: "Users", value: "users", route: "Users" },
      { icon: "mdi-widgets", title: "Widgets", value: "widgets", route: "Widgets" },
  ],
  rail: true,
  }
},
methods: {
    goTo(login) {
      // Lakukan aksi yang diinginkan ketika item di v-list diklik
      // Misalnya, navigasi ke halaman tertentu berdasarkan routeName
      this.navigasi = login;
      console.log('Navigating to', this.navigasi+' Coy!');
    },
  },
});

</script>