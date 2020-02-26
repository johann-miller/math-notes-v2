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
    .links {
        display: flex;
    }

    .links li:not(:first-child) {
        margin-left: 1rem;
    }

    nav {
        padding: 0.75rem;
        border-right: 1px #d6d9dc solid;
    }

    ul {
        list-style-type: none;
    }
</style>

<nav>
    <ul class="links">
        <li>
            <a href="/">Home</a>
        </li>
        <li>
            <a href="/">About</a>
        </li>
    </ul>
</nav>