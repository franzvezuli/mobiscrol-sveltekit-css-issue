<script lang="ts">
  import { eventcalendar, toast, util } from '@mobiscroll/javascript';
  import { onDestroy, onMount } from 'svelte';

  import '@mobiscroll/javascript/dist/css/mobiscroll.min.css';
  import {browser} from "$app/environment";

  let eventCalendarInstance;
  onMount(() => {
    console.log("Component mounted")
    eventCalendarInstance = eventcalendar('#calendar-1', {
      theme: 'material',
      themeVariant: 'light',
      clickToCreate: true,
      dragToCreate: true,
      dragToMove: true,
      dragToResize: true,
      eventDelete: true,
      view: {
        schedule: { type: 'week' },
      },
      onEventClick: function (event) {
        toast({
          message: event.event.title,
        });
      },
    });

    util.http.getJson(
        'https://trial.mobiscroll.com/events/?vers=5',
        function (events) {
          eventCalendarInstance.setEvents(events);
        },
        'jsonp',
    );
  });

  onDestroy( () => {
    if (browser) {
      console.log("Component removed")
      eventCalendarInstance.destroy()
    }
  });
</script>

<div id="calendar-1"></div>
