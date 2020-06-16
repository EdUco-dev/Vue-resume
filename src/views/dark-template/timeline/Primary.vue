<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        detailed   : true,
        year       : '2000-2003',
        transparent: true,
        title      : 'Administrator Network',
        html       : `
                <p>
                    Partner and network administrator at Plugginet Company. 
                    It was a small internet provider.
                </p>
                `,
        icon: 'mdi-console-network',
      },
      {
        year : '2003-2005',
        transparent: true,
        title: 'IT Analyst',
        html : `
                    <p>
                        Assigned to manage a Control Insured System and Payroll.
                    </p>
                    `,
       icon: 'mdi-desktop-classic',
      },
      {
        detailed   : true,
        year       : '2005-2017',
        transparent: true,
        title      : 'Customs IT Supervisor',
        /* eslint-disable no-useless-escape */
        html       : `
                <p>
                    Assigned to manage a Custom System.
                </p>
                <p>
                    Customs operations for Ford, Visteon, Linamar.
                </p>
                `,
        /* eslint-enable no-useless-escape */
        icon: 'mdi-database-lock',
      },
      
      {
        year : '2018',
        transparent: true,
        title: 'Project Certificates of Origin NAFTA',
        html : `
          <p>
            End Year Project to run and deliver Certificates of Origin for the year 2019.
          </p>
          `,
        iconImage: 'img/timeline/database-search.png',
      },
      {
        year : '2019',
        transparent: true,
        title: 'SAT Audit Project',
        html : `
          <p>
             Project to extract and compare data and delivered to Mexican Goverment. Project was sucessful and result was a tax refund.
          </p>
        `,
        iconImage: 'img/timeline/database-search.png',
      },
      {
        year : '2019',
        transparent: true,
        title: 'NAFTA-USMCA Project migration',
        html : `
          <p>
             Project to create and modify origin rules for the USMCA trade. 
         </p>
        `,
        image: 'img/timeline/nafta-usmca.png',
        icon : 'mdi-account-group',
      },
      {
        year : '2020',
        transparent: true,
        title: 'Web Developer Course',
        html : `
          <p>
              Taking a Web Course!
          </p>
          `,
        image    : 'img/timeline/certificate.png',
        iconImage: 'img/timeline/vue-registrar-logo.png',
      },
      {
        year : 'So far ...',
        title: 'Still learning about Web Development!',
        html : `Improve my skills in CSS and and discovering Vuejs!`,
        icon: 'mdi-fountain-pen-tip',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
