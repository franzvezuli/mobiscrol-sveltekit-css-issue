<script>
  import { goto } from '$app/navigation';

  function navigateToCalendarOne() {
    goto('/calendar-1');
  }

  function navigateToCalendarTwo() {
    goto('/calendar-2');
  }
</script>

<button on:click={navigateToCalendarOne}>Go to Calendar 1</button>
<button on:click={navigateToCalendarTwo}>Go to Calendar 2</button>

<slot />
