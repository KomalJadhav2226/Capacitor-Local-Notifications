<template>
  <q-page class="flex flex-center">
    <div>
      <q-btn label="Test" @click="scheduleNotification()"></q-btn>
    </div>
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
  </q-page>
</template>

<script>
import {defineComponent, onMounted} from 'vue';
import {LocalNotifications} from '@capacitor/local-notifications';
import {Plugins, Capacitor} from '@capacitor/core';

export default defineComponent({
  name: 'IndexPage',
  setup() {

    return {};
  },
  methods: {
    async scheduleNotification() {
      console.log(Capacitor, "capacitor")
      const {LocalNotifications} = Plugins;
        // Schedule a local notification
        LocalNotifications.schedule({
          notifications: [
            {
              title: 'My Notification',
              body: 'This is a local notification',
              id: 1,
              schedule: {at: new Date(Date.now() + 5000)},
              sound: null,
              attachments: null,
              actionTypeId: '',
              extra: null,
            },
          ],
        })
          .then(() => {
            console.log('Local notification scheduled');
          })
          .catch((error) => {
            console.error('Failed to schedule local notification:', error);
          });
      // } else {
      //   console.warn('LocalNotifications plugin is not available');
      // }
    },
  }
});


</script>
