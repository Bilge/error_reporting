<script lang="ts">
    let error_reporting: number;

    const error_levels = {
        E_ERROR:             1 << 0,
        E_WARNING:           1 << 1,
        E_PARSE:             1 << 2,
        E_NOTICE:            1 << 3,
        E_CORE_ERROR:        1 << 4,
        E_CORE_WARNING:      1 << 5,
        E_COMPILE_ERROR:     1 << 6,
        E_COMPILE_WARNING:   1 << 7,
        E_USER_ERROR:        1 << 8,
        E_USER_WARNING:      1 << 9,
        E_USER_NOTICE:       1 << 10,
        E_STRICT:            1 << 11,
        E_RECOVERABLE_ERROR: 1 << 12,
        E_DEPRECATED:        1 << 13,
        E_USER_DEPRECATED:   1 << 14,
        E_ALL:               (1 << 15) - 1,
    };
</script>

<main>
    <form>
        <input bind:value={error_reporting} placeholder="error_reporting">
        <ol>
        {#each Object.entries(error_levels) as [error, level]}
            <li class:active={error_reporting & level}>{error} <span>{level}</span></li>
        {/each}
        </ol>
    </form>
</main>

<style>
    main {
        display: flex;
        height: 100%;
        align-items: center;
        justify-content: center;
    }

    form {
        display: flex;
        flex-flow: column;
        align-items: center;
    }

    ol {
        display: flex;
        flex-flow: wrap;
        justify-content: center;
        max-width: 50em;
        gap: .5ex .5ch;
        padding: 0;

        font-size: 90%;
        list-style: none;
    }
    li {
        padding: .7ex .7ch;

        background: #eee;
        border-radius: 4px;
    }
    span {
        opacity: .7;
        font-size: 90%;
        letter-spacing: -.01em;
    }
    .active {
        color: #e1ffdd;
        background: #4ba83e;
    }
</style>
