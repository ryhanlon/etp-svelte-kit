<script>
    let subNavOpen;
    export let chapterLessons;
    export let url;
    export let isOpen;
    export let chapIndex;

    // $:console.log(chapterIndex, chapterLessons)
    const handleSubNav = () => {
        subNavOpen ? subNavOpen = false : subNavOpen = true;
    }
    export let chapterNum;

</script>

            <!--  SubNave Menu when Chapter is clicked  -->
            <button class="dropdown-btn"
                    on:click={handleSubNav}>{chapterNum}
                <i class="fa fa-caret-down"
                   class:fa-caret-up={subNavOpen} >
                </i>
            </button>
            <ul class="dropdown-container"
                 class:show-submenu={subNavOpen}>
                {#each chapterLessons as lessonObj, i}
            <!-- TODO on click is not rendering on li -->
                    <li on:click>
                        <a href={`${url}${lessonObj.slug}`}
                            data-chap-index={chapIndex}
                            data-lesson-index={i}>
                        {lessonObj.id} {lessonObj.engname}
                        </a>
                    </li>
                {/each}
            </ul>


<style>
    .dropdown-btn {
    padding: 6px 8px 6px 16px;
    text-decoration: none;
    font-size: 20px;
    color: #818181;
    display: block;
    border: none;
    background: none;
    width:100%;
    text-align: left;
    cursor: pointer;
    outline: none;
  }

  /* On mouse-over */
  .dropdown-btn:hover {
    color: #f1f1f1;
  }

  ul.dropdown-container {
    height: 0;
    overflow: hidden;
    background-color: #262626;
    padding-left: 8px;
      text-align: left;
  }

    ul.show-submenu {
        height: 150px;
        overflow: scroll;
    }

    li {
        margin: 5px 0;
        font-size: 1.1rem;
    }
    a {
        color: #a8a3a3;
    }

    /* Optional: Style the caret down icon */
    .fa-caret-down {
        float: right;
        padding-right: 8px;
    }

</style>