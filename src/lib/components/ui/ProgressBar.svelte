<script lang="ts">
	let { currentStep = $bindable(), totalSteps }: { currentStep: number; totalSteps: number } =
		$props();

	function navigateToStep(clickedStep: number) {
		if (clickedStep <= currentStep) {
			currentStep = clickedStep;
		}
	}
</script>

<div class="flex w-full gap-2">
	{#each Array(totalSteps) as _, i}
		{@const stepNumber = i + 1}
		<button
			class="flex h-1.5 w-1/5 rounded-md cursor-pointer relative border-transparent {currentStep >= stepNumber ? 'bg-blue-60' : 'bg-blue-20'}"
			onclick={() => navigateToStep(stepNumber)}
			aria-current={currentStep === stepNumber ? 'step' : undefined}
			aria-label={`Step ${stepNumber} of ${totalSteps}`}
		>
			
		</button>
	{/each}
</div>
