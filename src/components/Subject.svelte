<script>
    export let subject
    let expanded = false

    function expand() {
        expanded = !expanded
    }
</script>

<style>
    .arrow {
        filter: invert(20%) sepia(7%) saturate(259%) hue-rotate(2deg) brightness(100%) contrast(85%);
        transition: 0.1s transform ease-in-out;
        height: 1.5rem;
        width: auto;
    }

    .chapter:not(:last-child) {
        border-bottom: 1px #d6d9dc solid;
    }

    .chapter:not(:first-child) .chapter-title {
        padding-top: 0.5rem;
    }

    .chapters {
        background: #f0f0f0;
        padding: 0.5rem 1rem 0.5rem 1rem;
    }

    .expanded-arrow {
        transform: rotate(90deg)
    }

    .section {
        
        padding: 0.25rem 0 0.25rem 0.25rem;
    }

    .section a {
        font-weight: 300;
    }

    .subject-button {
        align-items: center;
        border: none;
        display: flex;
        justify-content: space-between;
        padding: 1rem;
        width: 100%;
    }
</style>

<li class="subject">
    <button class="subject-button" on:click={() => expand()}>
        {subject.title}
        <img src="images/arrow-right.svg" alt="arrow-right" class="arrow" class:expanded-arrow={expanded}>
    </button>
    {#if expanded}
        <ul class="chapters">
            {#each subject.chapters as chapter}
                <li class="chapter">
                    <div class="chapter-title">{chapter.title}</div>
                    <ul>
                        {#each chapter.sections as section}
                            <li class="section">
                                <a href="/posts/{section.post}">{section.title}</a>
                            </li>
                        {/each}
                    </ul>
                </li>
            {/each}
        </ul>
    {/if}
</li>