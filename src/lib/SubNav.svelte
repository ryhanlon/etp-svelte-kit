<script>
    export let subNavOpen;
    export let chapterLessons;
    export let url;

    // $:console.log(chapterIndex, chapterLessons)

    export let chapterNum;
    export let chapterIndex;

</script>

<!--  Chapter 1  -->
            <button class="dropdown-btn" >{chapterNum}
                <i class="fa fa-caret-down"
                   class:fa-caret-up={subNavOpen}
                   data-chapIndex={chapterIndex}
                   on:click >
                </i>
            </button>
            <div class="dropdown-container"
                 class:show-submenu={subNavOpen}>
                {#each chapterLessons as lessonObj}
                    <a on:click={() => isOpen = false} href={`${url}${lessonObj.slug}`}>
                        {lessonObj.id} {lessonObj.engname}
                    </a>
                {/each}
            </div>


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

  .dropdown-container {
    display: none;
    background-color: #262626;
    padding-left: 8px;
  }

    .show-submenu {
        height: 300px;
        overflow: scroll;
    }

    /* Optional: Style the caret down icon */
    .fa-caret-down {
        float: right;
        padding-right: 8px;
    }

</style>