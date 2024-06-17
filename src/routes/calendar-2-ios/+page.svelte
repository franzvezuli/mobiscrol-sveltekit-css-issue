<script lang="ts">
  import '@mobiscroll/javascript/dist/css/mobiscroll.min.css';
  import { onDestroy, onMount } from 'svelte';
  import { browser } from "$app/environment";
  import { eventcalendar } from '@mobiscroll/javascript';
  import type { Eventcalendar } from '@mobiscroll/javascript';

  let eventCalendarInstance: Eventcalendar;
  onMount(() => {
    eventCalendarInstance = eventcalendar('#calendar-2', {theme: 'ios'}) as Eventcalendar;
    console.log("Component mounted")
  });

  onDestroy( () => {
    if (browser) {
      eventCalendarInstance.destroy()
      console.log("Component removed")
    }
  });
</script>

<div id="calendar-2"></div>
