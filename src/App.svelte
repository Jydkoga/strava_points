<script>
	// Exported variables (if any) should be defined here
	export let user = "Guest";

	// Local component state or variables go here
	let exerciseGoals = [
		{
			name: "Cardio",
			description: "Improve cardiovascular health",
			completed: false,
		},
		{
			name: "Strength Training",
			description: "Build muscle strength",
			completed: false,
		},
		{
			name: "Flexibility",
			description: "Increase flexibility and mobility",
			completed: false,
		},
	];

	// Functions or other logic can be placed here
	function markCompleted(goal) {
		goal.completed = true;
	}
</script>

<main>
	<h1>Welcome, {user}!</h1>
	<p>Track your exercise goals and stay motivated!</p>

	{#if exerciseGoals.length > 0}
		{#each exerciseGoals as goal (goal.name)}
			<div class:goal={goal.completed}>
				<h3>{goal.name}</h3>
				<p>{goal.description}</p>
				{#if goal.completed}
					<p>Goal completed!</p>
				{:else}
					<button on:click={() => markCompleted(goal)}>Mark Completed</button>
				{/if}
			</div>
		{/each}
	{:else}
		<p>No exercise goals set yet. Start setting your goals now!</p>
	{/if}
</main>

<style>
	/* Add your styles here */
	h1 {
		color: #333;
	}

	.goal {
		margin-bottom: 20px;
		padding: 10px;
		border: 1px solid #ddd;
		border-radius: 5px;
	}

	.completed {
		background-color: #dff0d8;
		border-color: #d6e9c6;
		color: #3c763d;
	}
</style>
