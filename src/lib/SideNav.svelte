<script>
    import {fly} from 'svelte/transition';
    import SubNav from "./SubNav.svelte";

    export let isOpen;
    export let tocData;
    let chapterLesson1 = tocData[0].lessons;
    let chapterLesson2 = tocData[1].lessons;
    let chapterLesson3 = tocData[2].lessons;

    const url = "http://localhost:3000/exploring-the-path/";

    $:console.log(isOpen)
</script>


<nav class="topnav" id="topNav">
    <div>
        <h1>Exploring the Path</h1>
    </div>
    <!-- hamburger for modal   -->
    <div id="menu-cont" on:click={() => isOpen = true}>
        <a href="#menu" class="icon">
            &#9776;
        </a>
    </div>
</nav>


{#if isOpen}
    <section id="sidenav" class="sidenav" transition:fly={{x: 500}}>
        <a href="#navfauxlink" class="closebtn" on:click={() => isOpen = false}>&times;</a>

            <!--  Chapter 1  -->
            <SubNav chapterLessons={chapterLesson1}
                    {url}
                    {isOpen}
                    chapterNum="Chapter 1"
                    chapIndex="0"
                    on:click />

                    <!--  Chapter 2  -->
            <SubNav chapterLessons={chapterLesson2}
                    {url}
                    {isOpen}
                    chapterNum="Chapter 2"
                    chapIndex="1"
                    on:click />

                    <!--  Chapter 3  -->
            <SubNav chapterLessons={chapterLesson3}
                    {url}
                    {isOpen}
                    chapterNum="Chapter 3"
                    chapIndex="2"
                    on:click />

    </section>
{/if}


<style>
    nav {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
    }

    #menu-cont {
        position: absolute;
        top: 0;
        right: 0;
    }

    #menu-cont a{
        font-size: 1.8rem;

    }

    .topnav {
        overflow: hidden;
        background-color: #dcd3c0;
    }

    .topnav a {
        float: left;
        display: block;
        color: #333;
        text-align: center;
        padding: 14px 16px;
        text-decoration: none;
        font-size: 17px;
    }

    .topnav a:hover {
        background-color: #ddd;
        color: black;
    }


    .topnav .icon {
        display: block;
        float: right;
    }

    /* @media screen and (max-width: 600px) {
      .topnav a:not(:first-child) {display: none;}
      .topnav a.icon {
        float: right;
        display: block;
      }
    } */


    /* The side navigation menu */
    section.sidenav {
        height: 100%; /* 100% Full-height */
        width: 300px;
        position: fixed; /* Stay in place */
        z-index: 1; /* Stay on top */
        top: 0; /* Stay at the top */
        right: 0;
        background-color: #111; /* Black*/
        overflow-x: hidden; /* Disable horizontal scroll */
        padding-top: 60px; /* Place content 60px from the top */
        transition: 0.5s; /* 0.5 second transition effect to slide in the sidenav */
    }

    /* The navigation menu links */
    section.sidenav a {
        padding: 8px 8px 8px 32px;
        text-decoration: none;
        font-size: 1.1rem;
        color: #f1f1f1;
        display: block;
        cursor: pointer;
        transition: 0.3s;
    }

    .sidenav a {
        padding: 6px 8px 6px 16px;
        text-decoration: none;
        font-size: 20px;
        color: #818181;
        display: block;
        border: none;
        background: none;
        width: 100%;
        text-align: left;
        cursor: pointer;
        outline: none;
    }

    /* On mouse-over */
    .sidenav a:hover {
        color: #f1f1f1;
    }


    /*.show-submenu {*/
    /*    height: 300px;*/
    /*    overflow: scroll;*/

    /*}*/

    /* Optional: Style the caret down icon */


    section.sidenav .closebtn {
        position: absolute;
        top: 0;
        left: 0;
        font-size: 36px;
    }


    /* On smaller screens, where height is less than 450px, change the style of the sidenav (less padding and a smaller font size) */
    @media screen and (max-height: 450px) {
        section.sidenav {
            padding-top: 15px;
        }

        section.sidenav a {
            font-size: 18px;
        }
    }

</style>