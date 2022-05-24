<script>
    import {lessonsData} from '../../data/lessons_data.js';
	let chapterIndex = 0;
	let lessonIndex = 0;

    let  {slug, id, paliname, engname, definition } = lessonsData[chapterIndex].lessons[lessonIndex];

	export let hiLiteSel;

	const rootURL = 'http://localhost:3000/exploring-the-path/'

	const lessonLinks = ["Introduction", "English", "Pali", "Compare", "Flashcards"];
</script>


<header>
	<p class="pali">
		Namo tassa bhagavato arahato sammāsambuddhassa
	</p>
	<h3>{id}</h3>
	<h1 title={definition}>{paliname}</h1>
	<h2>{engname}</h2>

	<nav>
  {#each lessonLinks as linkName, i}
	  {#if i === 0}<a href={`${rootURL}${slug}/`}><button title={linkName}
						data-index={i}
						class:highlight={linkName === hiLiteSel}
						on:click>{linkName}</button></a>
		  {:else}
		  <a href={`${rootURL}${slug}/${linkName.toLowerCase()}`}><button title={linkName}
						data-index={i}
						class:highlight={linkName === hiLiteSel}
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