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
    .default-links {
        border-bottom: 2px #d6d9dc solid;
        display: flex;
        flex-flow: column;
        padding-bottom: 0.5rem;
    }

    nav {
        border-right: 1px #d6d9dc solid;
        height: 100vh;
        left: 0;
        padding: 1rem;
        position: fixed;
        top: 0;
        width: 18rem;

    }

    ul {
        list-style-type: none;
    }
</style>

<nav>
    <ul class="default-links">
        <li>
            <a href="/">Home</a>
        </li>
    </ul>
</nav>