<script>

</script>

<nav>
    <div class="over-view" data-current = "true">
        Overview
    </div>
    <div class="about" data-current="false">
        About
    </div>
</nav>

<style>

    nav {
        display: flex;
        justify-content: center;
        gap: 2em;
        margin: 7.5%;

        color: #4a4747f1;
        font-family: 'Raleway', sans-serif;
        font-size: 1.5rem;
    }

    nav > *:hover {
        color: white;
        transition: 0.25s cubic-bezier(.35,.14,.45,.25)
    }

    nav > *[data-current="true"] {
        color: white;
    }

</style>