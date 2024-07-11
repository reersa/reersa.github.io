<script setup>
import Tabs from 'primevue/tabs';
import TabList from 'primevue/tablist';
import Tab from 'primevue/tab';
import TabPanels from 'primevue/tabpanels';
import TabPanel from 'primevue/tabpanel';
import { ref } from 'vue';

const tabs = ref([
    { title: 'Home', value: '0' },
    { title: 'Our Story', value: '1' },
    { title: 'Photos', value: '2' },
    { title: 'Ceremony Details', value: '3' },
    { title: 'Travel/Hotel', value: '4' },
    { title: 'Registry', value: '5' },
    { title: 'FAQ', value: '6' },
]);
const selectedTab = ref(0);
const orientation = ref(0);

function SelectTab(tab)
{
  selectedTab.value = tab.value;
}

function isMobile() {
   if(/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
     return true;
   } else {
     return false;
   }
 }

 function isPortrait() {
    if (window.matchMedia("(orientation: portrait)").matches) {
      return true;
    } else {
      return false;
    }
 }
</script>

<template>
  <header>
    <meta name="color-scheme" content="light only">
    <img id="headerBackground" src="@/headerPicture.jpg"/>
    <span id="headerNames">Aaron & Falon</span>
  </header>
  <main>
    <Tabs id="headerTabs" value=0 scrollable=true>
      <TabList>
          <Tab v-for="tab in tabs" @click="SelectTab(tab);" style="width:100%" :key="tab.title" :value="tab.value">{{ tab.title }}</Tab>
      </TabList>
    </Tabs>
    <div>
      <div v-if="selectedTab == 0">
        <span>HomeHome</span>
      </div>
      <div v-if="selectedTab == 1">
        <span>Our Story</span>
      </div>
      <div v-if="selectedTab == 2">
        <span>Photos</span>
      </div>
      <div v-if="selectedTab == 3">
        <span>Ceremony Details</span>
      </div>
      <div v-if="selectedTab == 4">
        <span>Travel/Hotel</span>
      </div>
      <div v-if="selectedTab == 5">
        <span>Registry</span>
      </div>
      <div v-if="selectedTab == 6">
        <span>FAQ</span>
      </div>
    </div>
  </main>
</template>