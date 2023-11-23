<script lang="ts">
  import { eventcalendar, toast, util } from '@mobiscroll/javascript';
  import { onMount } from 'svelte';

  import '@mobiscroll/javascript/dist/css/mobiscroll.min.css';

  onMount(() => {
    const inst = eventcalendar('#calendar-2', {
      theme: 'ios',
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
          inst.setEvents(events);
        },
        'jsonp',
    );
  });
</script>

<div id="calendar-2"></div>
