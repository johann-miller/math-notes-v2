<script>
    let subjects = [
        {
            title: "Subject 1"
        },
        {
            title: "Subject 2"
        },
        {
            title: "Subject 3"
        },
    ]
</script>

<style>
    nav {
        border-right: 1px #d6d9dc solid;
        height: 100vh;
        left: 0;
        position: fixed;
        top: 0;
        width: 16rem;

    }

    ul {
        list-style-type: none;
    }

    .arrow {
        filter: invert(20%) sepia(7%) saturate(259%) hue-rotate(2deg) brightness(100%) contrast(85%);
        transition: 0.1s transform ease-in-out;
        height: 1.5rem;
        width: auto;
    }

    .default-links {
        border-bottom: 3px #d6d9dc solid;
        display: flex;
        flex-flow: column;
        padding-bottom: 0.5rem;
        margin: 1rem;
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

<nav>
    <ul class="default-links">
        <li>
            <a href="/">Home</a>
        </li>
    </ul>
    <ul>
        {#each subjects as subject}
            <li class="subject">
                <button class="subject-button">
                    {subject.title}
                    <img src="images/arrow-right.svg" alt="arrow-right" class="arrow">
                </button>
                
            </li>
        {/each}
    </ul>
</nav>