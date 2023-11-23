<script>
    import { goto } from '$app/navigation';

    function navigateToCalendarOne() {
        goto('/calendar-1-material');
    }

    function navigateToCalendarTwo() {
        goto('/calendar-2-ios');
    }
</script>

Switch between calendar views
<br/>

<button on:click={navigateToCalendarOne}>Go to Calendar 1 (Material)</button>
<button on:click={navigateToCalendarTwo}>Go to Calendar 2 (iOS)</button>

<slot />
