<script>
    import { readTextFile } from '@tauri-apps/api/fs';
    import { open } from '@tauri-apps/api/dialog';

    let contents;

    async function openFile() {
        const file = await open({
            multiple: false,
            directory: false,
        });

        contents = await readTextFile(file);
    }
</script>

<button on:click={openFile}> Open File </button>

{#if contents}
    <pre>{contents}</pre>
{/if}
