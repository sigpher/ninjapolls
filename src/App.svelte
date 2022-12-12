<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import PollList from "./components/PollList.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import Tabs from "./shared/Tabs.svelte";

	let items = ["Current Polls", "Add New Poll"];
	let activeItem = "Current Polls";
	const tabChange = (e) => {
		activeItem = e.detail;
	};
	//已经转移到store
	// let polls = [
	// 	{
	// 		id: 1,
	// 		question: "Python or JavaScript?",
	// 		answerA: "Python",
	// 		answerB: "JavaScript",
	// 		votesA: 9,
	// 		votesB: 15,
	// 	},
	// ];

	const handleAdd = (e) => {
		// const poll = e.detail;
		// polls = [poll, ...polls];
		// console.log(polls);
		activeItem = "Current Polls";
	};

	// const handleVote = (e) => {

	// };

	// import { tweened } from "svelte/motion";
	// const value = tweened(0);
</script>

<!-- <button
	on:click={() => {value.set(1);
	}}>{$value}</button
> -->

<Header />

<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange} />
	{#if activeItem === "Current Polls"}
		<PollList />
	{:else if activeItem === "Add New Poll"}
		<CreatePollForm on:add={handleAdd} />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
