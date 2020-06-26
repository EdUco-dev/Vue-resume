<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="Who am I?"
      >
        I'm a developer born in Mexico
        I'm interested and skilled in different topics of Information Technology like consulting and web development.
      </content-section>
      <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon: 'mdi-help-rhombus-outline',
        text: 'Data and Reporting Specialist for SAT (Servicio Administracion Tributaria) Audit at DXC Technologies',
        // source: '(Bytegate.ir post views)',
      },
      {
        icon: 'mdi-library-music',
        text: 'Analyst Senior migration NAFTA-USMCA Trades at DXC Technologies',
        // source: '(Bobet.ir and its channel downloads)',
      },
      {
        icon: 'mdi-timer-sand',
        text: 'Analyst Senior for NAFTA operations at DXC Technologies',
        // source: '(Delix.ir service usages)',
      },
    ],
    educations: [
      {
        from    : '2011',
        to      : '2012',
        title   : 'Master\'s degree, Information Technology Management',
        location: 'Universidad TecMilenio',
      },
    ],
    skills: [
      {
        title: 'SQL',
        icon : 'mdi-database',
        value: 70,
      },
      {
        title: 'HTML',
        icon : 'mdi-language-html5',
        value: 50,
      },
      {
        title: 'CSS',
        icon : 'mdi-language-css3',
        value: 50,
      },
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 50,
      },
      {
        title: 'Vue.js Framework',
        icon : 'mdi-vuejs',
        value: 50,
      },
      {
        title: 'React.js Framework',
        icon : 'mdi-react',
        value: 50,
      },
      { divider: true },
      {
        title: 'Heroku',
        icon : 'mdi-shield-lock',
        value: 50,
      },
      {
        title: 'Node',
        icon : 'mdi-shield-lock',
        value: 50,
      },

      {
        title: 'Git',
        icon : 'mdi-git',
        value: 60,
      },
      { divider: true },

      {
        title: 'Leadership',
        icon : 'mdi-account-group',
        value: 60,
      },
      {
        title: 'Linux',
        icon : 'mdi-arch',
        value: 60,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
