<script lang="ts">
    let { id, name, value, onchange }: { id?: string; name?: string; value?: string, onchange?: () => void } = $props();
</script>

<div class="border border-blue-60 flex gap-1 items-center justify-center w-fit p-1.5 rounded-lg cursor-pointer">
	<input type="checkbox" {id} {name} {value} class="border-blue-60 accent-bg-60 bg-blue-60 "/>
			<label for={id} class="text-sm">{name}</label>
</div>