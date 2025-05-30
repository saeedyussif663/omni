<script>
 import ComponentPreview from '$lib/components/component-preview/component-preview.svelte';
 import InstallationSnippets from '$lib/components/installation-snippets/installation-snippets.svelte';
</script>

# Avatar

A customizable avatar component for your SvelteKit app.

<br/>

<ComponentPreview name="Avatar" />

## Setting Up

This component is standalone and does not require additional dependencies. You can directly copy and use it in your project.

<br/>

Copy the `<Avatar/>` component:

```ts
<script lang="ts">
    const {src, fallbackText} = $props()
    let imageLoaded = $state(false)
</script>

<div class="size-11 border flex items-center justify-center rounded-full">
    {#if !imageLoaded}
        <span>{fallbackText}</span>
    {/if}
    <img
        src={src}
        alt={fallbackText}
        class="!rounded-full w-full h-full"
        class:hidden={!imageLoaded}
        onload={() => {
            imageLoaded = true
        }}
    />
</div>
```

## Usage Example

Here’s how you can use the `<Avatar/>` component in your project:

```ts
<script lang="ts" module>
	import Avatar from "./avatar.svelte";
</script>

<Avatar src="https://avatars.githubusercontent.com/u/73991180" fallbackText="TB"/>
```
