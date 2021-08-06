<template>
  <v-app>
    <v-main>
      <v-layout style="justify-content: space-between">
        <v-card>
          <v-navigation-drawer v-model="drawer" permanent>
            <v-list-item>
              <v-list-item-avatar> </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title style="color: purple; font-size: 20px"
                  >Konnexion</v-list-item-title
                >
              </v-list-item-content>
            </v-list-item>

            <v-list>
              <v-list-item v-for="item in items2" :key="item.title">
                <v-list-item-icon style="padding-left: 10px">
                  <v-icon>{{ item.icon }}</v-icon>
                </v-list-item-icon>

                <v-list-item-content style="padding-left: 10px">
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list>
              <v-list-group
                dense
                v-for="item in items"
                :key="item.title"
                v-model="item.active"
                :prepend-icon="item.action"
                no-action
              >
                <template v-slot:activator>
                  <v-list-item-content style="margin-left: -20px">
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                  </v-list-item-content>
                </template>

                <v-list-item
                  v-for="child in item.items"
                  :key="child.title"
                  dense
                >
                  <v-list-item-icon>
                    <v-icon :color="child.color">{{ child.action }}</v-icon>
                  </v-list-item-icon>
                  <v-list-item-content style="margin-left: -20px">
                    <v-list-item-title> {{ child.title }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-group>
            </v-list>
          </v-navigation-drawer>
        </v-card>
        <v-card>
          <v-navigation-drawer
            v-model="drawer2"
            mini-variant
            permanent
            right
            color="#981CEB"
          >
            <v-list-item class="px-2">
              <v-list-item-avatar>
                <v-img
                  src="https://randomuser.me/api/portraits/men/85.jpg"
                ></v-img>
              </v-list-item-avatar>

              <v-list-item-title>John Leider</v-list-item-title>

              <v-btn icon @click.stop="mini = !mini">
                <v-icon>mdi-chevron-left</v-icon>
              </v-btn>
            </v-list-item>

            <v-divider></v-divider>

            <v-list dense>
              <v-list-item v-for="item in items3" :key="item.title" link>
                <v-list-item-icon>
                  <v-icon color="white">{{ item.icon }}</v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-navigation-drawer>
        </v-card>
      </v-layout>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data() {
    return {
      drawer2: true,
      items3: [
        { title: "a", icon: "mdi-email-outline" },
        { title: "b", icon: "mdi-message-processing-outline" },
        { title: "c ", icon: "mdi-arrow-down-box" },
        { title: "d", icon: "mdi-video-outline" },
        { title: "e", icon: "mdi-clipboard-outline" },
        { title: "f", icon: "mdi-clock-time-two-outline" },
        { title: "g", icon: "mdi-calculator" },
        { title: "h", icon: "mdi-help" },
      ],
      mini: true,

      drawer: null,
      items2: [
        { title: "Set up", icon: "mdi-tune-variant" },
        { title: "Tableau de bord", icon: "mdi-view-dashboard-outline" },
        { title: "Calendrier", icon: "mdi-calendar-blank-outline" },
        { title: "Gantt", icon: "mdi-chart-gantt" },
      ],
      items: [
        {
          action: "mdi-account-group-outline",
          items: [
            { action: "mdi-trello", title: "Opportunités", color: "yellow" },
            { action: "mdi-account", title: "Prospects" },
            { action: "mdi-cube", title: "Produits" },
          ],
          title: "Relation Client",
        },
        {
          action: "mdi-layers-triple-outline",
          active: true,
          items: [
            { title: "Projet", action: "mdi-layers" },
            { title: "Fichier", action: "mdi-file" },
            { title: "Congés", action: "mdi-timer-sand-empty" },
            { title: "Annonces", action: "mdi-newspaper-variant-outline" },
          ],
          title: "Gestion de Projet",
        },
        {
          action: "mdi-receipt",
          title: "Stock & Facturation",
        },
        {
          action: "mdi-currency-eur",
          title: "Coordination financière",
        },
        {
          action: "mdi-account-cog",
          title: "Ressources  humaines",
        },
      ],
    };
  },
};
</script>
