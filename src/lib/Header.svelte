<script>
    import {lessonsData} from '../routes/exploring-the-path/lessons_data.js';
    const {id, paliname, engname, definition } = lessonsData.lesson_1.ln_1_1_1;
    console.log(lessonsData, 'test');
	export let hiLiteSel;

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
		<button title={linkName}
						data-index={i}
						class:highlight={linkName === hiLiteSel}
						on:click>{linkName}</button>
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