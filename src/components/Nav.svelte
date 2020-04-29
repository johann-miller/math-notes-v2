<script>
    import Subject from "./Subject.svelte"

    let subjects = [
        {
            title: "Subject 1",
            chapters: [
                {
                    title: "Chapter 1",
                    sections: [
                        {title: "Section 1", postID: "aZdNJyvwLRziWCy8iXgW"},
                        {title: "Section 2", postID: "VbVuC3eDHSt6ngWPfDje"},
                        {title: "Section 3", postID: "aZdNJyvwLRziWCy8iXgW"},
                    ]
                },
                {
                    title: "Chapter 2",
                    sections: [
                        {title: "Section 1", postID: "aZdNJyvwLRziWCy8iXgW"},
                        {title: "Section 2", postID: "aZdNJyvwLRziWCy8iXgW"},
                        {title: "Section 3", postID: "aZdNJyvwLRziWCy8iXgW"},
                    ]
                },
                {
                    title: "Chapter 3",
                    sections: [
                        {title: "Section 1", postID: "aZdNJyvwLRziWCy8iXgW"},
                        {title: "Section 2", postID: "aZdNJyvwLRziWCy8iXgW"},
                        {title: "Section 3", postID: "aZdNJyvwLRziWCy8iXgW"},
                    ]
                },
            ]
        },
        {
            title: "Subject 2",
            chapters: [
                {
                    title: "Chapter 1",
                    sections: [
                        {title: "section 1"},
                        {title: "section 2"},
                        {title: "section 3"},
                    ]
                },
                {
                    title: "Chapter 2",
                    sections: [
                        {title: "section 1"},
                        {title: "section 2"},
                        {title: "section 3"},
                    ]
                },
                {
                    title: "Chapter 3",
                    sections: [
                        {title: "section 1"},
                        {title: "section 2"},
                        {title: "section 3"},
                    ]
                },
            ]
        },
        {
            title: "Subject 3",
            chapters: [
                {
                    title: "Chapter 1",
                    sections: [
                        {title: "section 1"},
                        {title: "section 2"},
                        {title: "section 3"},
                    ]
                },
                {
                    title: "Chapter 2",
                    sections: [
                        {title: "section 1"},
                        {title: "section 2"},
                        {title: "section 3"},
                    ]
                },
                {
                    title: "Chapter 3",
                    sections: [
                        {title: "section 1"},
                        {title: "section 2"},
                        {title: "section 3"},
                    ]
                },
            ]
        },
    ]
</script>

<style>
    nav {
        border-right: 1px #d6d9dc solid;
        height: 100%;
        width: 100%;
        max-height: 100vh;
        overflow-y: scroll;

    }

    ul {
        list-style-type: none;
    }

    .default-links {
        border-bottom: 2px #d6d9dc solid;
        display: flex;
        flex-flow: column;
        padding-bottom: 0.5rem;
        margin: 1rem;
    }

    .menu {
        background: #fcfcfc;
        border: none;
        display: none;
        left: 16.5rem;
        opacity: 0.5;
        padding: 0.5rem;
        position: absolute;
        top: 0.75rem;
        z-index: 1;
    }

    .menu img {
        filter: invert(20%) sepia(7%) saturate(259%) hue-rotate(2deg) brightness(100%) contrast(85%);
        height: 1.5rem;
        width: auto;
    }
</style>

<nav>
    <button class="menu">
        <img src="images/menu.svg" alt="Menu">
    </button>
    <ul class="default-links">
        <li>
            <a href="/">Home</a>
        </li>
    </ul>
    <ul>
        {#each subjects as subject}
            <Subject subject={subject}/>
        {/each}
    </ul>
</nav>