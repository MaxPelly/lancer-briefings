<template>
  <Header :header="this.header" />
  <div class="content-container">
    <section class="section-container" id="missions" style="width:22.87vw; height:78.46vh; min-width:300px; min-height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/mission-icon.svg" />
        <h1>Mission Log</h1>
      </div>
      <div class="section-content-container">
        <h3>Current Assignment</h3>
        <Markdown :source="current_md" class="markdown" />
        <h3>Mission List</h3>
        <div class="mission-list-container">
          <Mission
            v-for="item in this.missions"
            :key="item.slug"
            :mission="item"
            :selected="this.mission_slug"
            @click="selectMission(item)"
          />
        </div>
      </div>
    </section>
    <section class="section-container" id="events" style="width:22.87vw; height:78.46vh; min-width:300px; min-height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/events-icon.svg" />
        <h1>Events Log</h1>
      </div>
      <div class="section-content-container">
        <Markdown :source="events" class="markdown" />
      </div>
    </section>
    <section class="section-container" id="pilots" style="width:37vw; height:78.46vh; min-width:600px; min-height:714px; max-width:850px;">
    <div style="height:52px; overflow:hidden;">
        <div class="section-header clipped-medium-backward-pilot">
          <img src="/icons/pilot-icon.svg" />
          <h1>Pilot Roster</h1>
        </div>
        <div class="rhombus-back">&nbsp;</div>
	</div>
      <div class="section-content-container">
        <div class="pilot-list-container">
          <Pilot v-for="item in this.pilots" :key="item.slug" :pilot="item" />
        </div>
      </div>
    </section>
  </div>
  <svg
    style="visibility: hidden; position: absolute;"
    width="0"
    height="0"
    xmlns="http://www.w3.org/2000/svg"
    version="1.1"
  >
    <defs>
      <filter id="round">
        <feGaussianBlur in="SourceGraphic" stdDeviation="5" result="blur" />
        <feColorMatrix
          in="blur"
          mode="matrix"
          values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -5"
          result="goo"
        />
        <feComposite in="SourceGraphic" in2="goo" operator="atop" />
      </filter>
    </defs>
  </svg>
  <audio autoplay>
    <source src="/startup.ogg" type="audio/ogg" />
  </audio>
  <Footer/>
</template>

<script>
import Header from './components/layout/Header.vue';
import Footer from './components/layout/Footer.vue';
import Mission from './components/Mission.vue';
import Pilot from './components/Pilot.vue';
import Markdown from 'vue3-markdown-it';

export default {
  components: {
    Header,
    Footer,
    Mission,
    Pilot,
    Markdown
  },

  data() {
    return {
      "mission_slug": "006",
      "current_md": "006",
      "events": "",
      "missions": [
          {
          "slug": "001",
          "name": "A Little Bit Damp",
          "status": "success"
        },
	    {
          "slug": "002",
          "name": "Signals Left Unsung",
          "status": "success"
        },
	    {
          "slug": "003",
          "name": "Operation Howling Blade",
          "status": "success"
        },
        {
          "slug": "004",
          "name": "Budding Problems",
          "status": "success"
        },
        {
          "slug": "005",
          "name": "Exploring Astran IV",
          "status": "success"
        },
        {
          "slug": "006",
          "name": "Small Problem - Quick Solution",
          "status": "start"
        },
      ],
      "pilots": [
{
	"callsign": "Monkey",
	"alias": "Sophia Ogawa",
	"code": "bbede182-f785-4627-b36c-05c3fa1dde0f",
	"corpo": "SSC",
	"frame": "black witch alt orchidea",
	"mech": "Arcturus"
},
{
	"callsign": "HACKERMANS.omif",
	"alias": "Ecne",
	"code": "608020a8-d694-4d4b-a93e-d62a64172212",
	"corpo": "HORUS",
	"frame": "hydra",
	"mech": "Monsus the Battle Bus"
},
{
	"callsign": "Charon",
	"alias": "Kere Feldston",
	"code": "b78cb30e-c0c4-46fe-bfa1-5b29cf95cb01",
	"corpo": "HORUS",
	"frame": "gorgon",
	"mech": "SCREAM HER NAME"
},
{
	"callsign": "Birdy",
	"alias": "Alison Rosalyn Hawk   ",
	"code": "f82bed86-0e32-4b9d-a884-3f06c73e59cb",
	"corpo": "HORUS",
	"frame": "balor",
	"mech": "E.T.N.A."
},
{
	"callsign": "MIRAGE",
	"alias": "Avron Aubery",
	"code": "6ccc5d00-2315-4343-8c5f-fb75f336ef83",
	"corpo": "IPS-N",
	"frame": "zheng",
	"mech": "A Gentelman Will Walk But Never Run"
},
{
	"callsign": "Lockjaw",
	"alias": "Rinea Farthing",
	"code": "9a8a5302-b10d-4824-a07a-6bd979db6fee",
	"corpo": "IPS-N",
	"frame": "blackbeard",
	"mech": "If it was a good morning, I'd be grappling"
},
{
	"callsign": "Badger",
	"alias": "Darragh Black",
	"code": "7fff6993-18f0-4711-b4ad-d530cced8981",
	"corpo": "GMS",
	"frame": "standard pattern i everest",
	"mech": "In Search Of Elusive Little Comets"
},
{
	"callsign": "HB",
	"alias": "Honey",
	"code": "3c77860d-7c05-4b79-8021-31d83cac1353",
	"corpo": "GMS",
	"frame": "chomolungma",
	"mech": "Discord Kitten"
},
{
	"callsign": "Foundryside",
	"alias": "Gregor Vancil",
	"code": "c8dc2f82-c0bf-42d7-a00f-583b55fb892e",
	"corpo": "GMS",
	"frame": "standard pattern i everest",
	"mech": "General. Ambulatory. Repair. Loader"
},
{
	"callsign": "Khepri",
	"alias": "Faramarz Assalon",
	"code": "0accf271-4128-4488-a6ad-3ad72b79a335",
	"corpo": "GMS",
	"frame": "standard pattern i everest",
	"mech": "Evolution By Shock"
},
{
	"callsign": "Ember",
	"alias": "Ellis Coen",
	"code": "e5c3a5e7-39a1-49a4-9155-c184a0d770a3",
	"corpo": "GMS",
	"frame": "chomolungma",
	"mech": "Mechy McMechface"
},
{
	"callsign": "Castlefall",
	"alias": "Randalla",
	"code": "5efa3efa-9f63-4680-bc99-84198b8f27d8",
	"corpo": "GMS",
	"frame": "standard pattern i everest",
	"mech": "Apologies in Advance"
},
{
	"callsign": "Count",
	"alias": "Cresla Major",
	"code": "88a39b8a-1a60-48f6-8133-184f2de947ee",
	"corpo": "GMS",
	"frame": "standard pattern i everest",
	"mech": "Wensleydale"
},
],
      "header": {
        "planet": "Astran IV",
        "year": "5014u",
        "system": "<Redacted>",
        "gate": "<Redacted>",
        "ring": "<Redacted>",
        "headerTitle": "Mirrorsmoke",
        "headerSubtitle": "Mercenary Company",
        "subheaderTitle": "Worlds End",
        "subheaderSubtitle": "Delta-Echo-Echo-Zulu",
      },
      "options":{
        "eventsMarkdownPerMission": true
      }
    }
  },

  created() {
    this.loadMissionMarkdown()
    this.loadEventsMarkdown()
  },

  computed: {

  },

  methods: {
    selectMission(mission) {
      this.mission_slug = mission.slug;
      this.loadMissionMarkdown()
      if(this.options.eventsMarkdownPerMission){
        this.loadEventsMarkdown();
      }
    },
    loadMissionMarkdown() {
      let self = this;
      let md = `/missions/${self.mission_slug}.md`
      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.current_md = client.responseText;
      }
      client.send();
    },
    loadEventsMarkdown() {
      let self = this;
      let md = "";

      if(self.options.eventsMarkdownPerMission){
        md = `/events/${self.mission_slug}.md`
      }
      else {
        md = "/events.md"
      }

      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.events = client.responseText;
      }
      client.send();
    }
  }

}
</script>


<style lang="scss">
#app {
  width: 100vw;
  height: 100vh;
  min-width: 1300px;
  min-height: 910px;
  overflow: hidden;
}
</style>
