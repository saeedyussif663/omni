<script lang="ts">
	import { cn } from "$lib/utils/cn";
	import { cva } from "class-variance-authority";
    import type { HTMLAttributes } from "svelte/elements";

    let imageLoaded = $state(false)
    
    type Props = HTMLAttributes<HTMLDivElement> & {
        class?: string;
        src: string,
        fallbackText: string
    };
    
    const {src, fallbackText, class: className, ...props}: Props = $props()
</script>

<div class={cn("size-11 border flex items-center justify-center rounded-full", cva({ className }))} {...props}>
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