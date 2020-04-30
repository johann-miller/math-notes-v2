<script>
    import {onMount} from 'svelte'
    import Subject from "./Subject.svelte"

    let subjects = []

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