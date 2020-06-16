<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Edgar <span class="light-blue--text text--lighten-3">Uco</span>
        </h1>
        <span>
          A challenge-loving web developer
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'edgar.uco.gomez@gmail.com',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'github',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'Jun 3, 1973',
            },
            {
              name: 'Location',
              icon: 'mdi-map-marker',
              text: 'Miwaukee, USA',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/EdUco-dev',
              link: 'https://github.com/EdUco-dev',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/edgar-uco',
              link: 'linkedin.com/in/edgar-uco-3949b35a',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [
            {
              icon: 'mdi-movie',
              text: 'movies',
            },
            {
              icon: 'mdi-feature-search',
              text: 'research',
            },
            {
              icon: 'mdi-run',
              text: 'running',
            },
            {
              icon: 'mdi-airplane',
              text: 'traveling',
            },
            {
              icon: 'mdi-chef-hat',
              text: 'cooking',
            },
            {
              icon: 'mdi-music',
              text: 'music',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'English',
              value: 60,
            },
            {
              text : 'Spanish',
              value: 100,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #2e2e2e;
}
</style>
