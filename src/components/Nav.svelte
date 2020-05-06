<script>
    import {onMount} from 'svelte'
    import Subject from "./Subject.svelte"

    let subjects = []
    let navClosed = true

    onMount(() => {
        let db = firebase.firestore()

        db.collection("subjects").get().then((querySnapshot) => {
            subjects = []

            querySnapshot.forEach((doc) => {
                let subject = doc.data()
                subjects.push(subject)
            })

            subjects.sort()
            subjects = subjects
        })
    })

    function toggleNav() {
        navClosed = !navClosed
    }
</script>

<style>
    nav {
        background: #FFFCF8;
        border-right: 2px #d6d9dc solid;
        height: 100vh;
        width: 100vw;
        max-height: 100vh;
        max-width: 20rem;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 1;
        overflow-y: scroll;
        transition: 0.1s left ease-in-out;
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
        background: #FFFCF8;
        border: none;
        left: 0.5rem;
        opacity: 0.7;
        padding: 0.75rem;
        position: fixed;
        bottom: 0.75rem;
        z-index: 1;
    }

    .menu img {
        filter: invert(20%) sepia(7%) saturate(259%) hue-rotate(2deg) brightness(100%) contrast(85%);
        height: 1.5rem;
        width: auto;
        margin-right: 0.5rem;
    }

    .closed {
        left: -20rem;
    }

    @media only screen and (min-width: 900px) {
        .closed {
            left: 0;
        }

        nav {
            position: relative;
            border-right: 1px #d6d9dc solid;
            height: 100%;
            width: 100%;
        }

        .menu {
            display: none;
        }
    }
</style>

<nav class:closed={navClosed}>
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
<button class="menu" on:click={toggleNav}>
    <img src="images/menu.svg" alt="Menu">
    Menu
</button>