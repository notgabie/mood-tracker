<script lang="ts">
	import ProgressBar from './ui/ProgressBar.svelte';
	import TagLabel from './ui/TagLabel.svelte';

	let step = $state<1 | 2 | 3 | 4>(1);
	let moodSelections = $state<Array<{
		mood: string;
		tags: string[];
		sleepQuality: string;
	}>>([
		{
			mood: '',
			tags: [],
			sleepQuality: ''
		}
	])

	let moods = [
		'Very Happy',
		'Happy',
		'Neutral',
		'Sad',
		'Very Sad'
	];
	let tags = [
		'Joyful',
		'Down',
		'Anxious',
		'Calm',
		'Excited',
		'Frustrated',
		'Lonely',
		'Grateful',
		'Overwhelmed',
		'Motivated',
		'Irritable',
		'Peaceful',
		'Tired',
		'Hopeful',
		'Confident',
		'Stressed',
		'Content',
		'Disappointed',
		'Optimistic',
		'Restless'
	];
	let selectedTags: string[] = [];

</script>

<section>
	<h2>Log your mood</h2>
	<p>Step: {step}</p>
	<ProgressBar bind:currentStep={step} totalSteps={4} />
	{#if step === 1}
		<p>How was your mood today?</p>
		<fieldset>
			{#each moods as mood} 
				<input type="radio" id={mood.toLowerCase().replace(' ', '-')} name="mood" value={mood} />
				<label for={mood.toLowerCase().replace(' ', '-')}>{mood}</label>
			{/each}
		</fieldset>
	{:else if step === 2}
		<p>How did you feel?</p>
		<fieldset class="flex flex-wrap gap-2">
			{#each tags as tag}
				<TagLabel id={tag} name={tag} value={tag} onchange={() => {
						if (selectedTags.includes(tag)) {
							selectedTags = selectedTags.filter((t) => t !== tag);
						} else {
							selectedTags = [...selectedTags, tag];
						}
				}}/>
			{/each}
		</fieldset>
	{:else if step === 3}
		<p>How well did you sleep?</p>
	{/if}
	{#if step < 3}
    <button onclick={()=> step < 4 ? step = step + 1 : step = 4}>Continue</button>
	{:else}
		<button>Submit</button>
	{/if}
</section>
