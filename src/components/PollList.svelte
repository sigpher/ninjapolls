<script>
    import { fade, slide, scale } from "svelte/transition";
    import { flip } from "svelte/animate";
    // import { onDestroy, onMount } from "svelte";
    import PollStore from "../stores/PollStore";
    import PollDetails from "./PollDetails.svelte";

    //用$PollStore代替以下这么多行
    // export let polls = [];
    // const unsub = PollStore.subscribe((data) => {
    //     polls = data;
    // });

    // onMount(() => {
    //     console.log("component mounted");
    // });
    // onDestroy(() => {
    //     console.log("component destroy");
    //     unsub();
    // });
</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <!-- <div in:fade out:slide> -->
        <div in:fade out:scale|local animate:flip={{ duration: 500 }}>
            <PollDetails {poll} />
        </div>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
