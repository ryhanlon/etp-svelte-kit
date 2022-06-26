<script>
    import {lessonsData} from '../routes/data/lessons_data.js';
	import SideNav from "./SideNav.svelte";

	// TODO make header button dynamic

	let chapIndex = 0;
	let lessonIndex = 0;
   $: lesson = lessonsData[chapIndex].lessons[lessonIndex];

	const setIndices = (e) => {
		chapIndex = e.target.dataset.chapIndex;
		lessonIndex = e.target.dataset.lessonIndex;
	}

	const rootURL = 'http://localhost:3000/exploring-the-path/'

	const lessonLinks = ["Introduction", "English", "Pali", "Compare", "Flashcards"];

	let isOpen = false;
	let subNavOpen = false;
	// $: console.log(lesson);
</script>


<header>
	<SideNav {isOpen}
			 {subNavOpen}
			 tocData={lessonsData}
			 on:click={setIndices} />
	<p class="pali">
		Namo tassa bhagavato arahato sammāsambuddhassa
	</p>
	<h3>{lesson.id}</h3>
	<h1 title={lesson.definition}>{lesson.paliname}</h1>
	<h2>{lesson.engname}</h2>

	<nav>
  {#each lessonLinks as linkName, i}
	  {#if i === 0}<a href={`${rootURL}${lesson.slug}/`}><button title={linkName}
						data-index={i}
						on:click>{linkName}</button></a>
		  {:else}
		  <a href={`${rootURL}${lesson.slug}/${linkName.toLowerCase()}`}><button title={linkName}
						data-index={i}
						on:click>{linkName}</button></a>
		  {/if}
	{/each}
</nav>
</header>


<style>
	header {
		text-align: center;
		padding: 1rem 0.5rem;
		background-color: #dcd3c0;
	}

	h1, h2, h3 {
		margin: 5px;
	}

	h1 {
		font-size: 1.4rem
	}
	h2 {
		font-size: 1.2rem
	}
	h3 {
		font-size: 1rem
	}

	p {
		margin: 0;
	}

	.pali {
		font-style: italic;
		font-size: .8rem
	}

	nav {
		margin: 10px 0 0 0 ;
		padding: 0;
	}
	button {
		border: none;
    border-radius: 5px;
    background: #ba5626;
    font-size: 1rem;
    color: white;
    width: 105px;
		margin: 10px 10px 0;
		cursor: pointer;
	}

	.highlight {
		background: #1372BA;
	}
<!--</style>