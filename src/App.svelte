<script>
    import { readTextFile } from '@tauri-apps/api/fs';
    import { open } from '@tauri-apps/api/dialog';

    /** @type {string} */
    let contents;

    async function openFile() {
        const file = await open({
            multiple: false,
            directory: false,
        });

        if (typeof file != 'string') {
            // No file given (also file won't be an array of strings here since multiple is false)
            return;
        }

        contents = await readTextFile(file);
    }
</script>

<button on:click={openFile}> Open File </button>

{#if contents}
    <pre>{contents}</pre>
{/if}
