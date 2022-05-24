<script>
    import {lessonsData} from '../../../../../data/lessons_data.js';
	let chapterIndex = 0;
	let lessonIndex = 0;

	let sidebysideData = lessonsData[chapterIndex].lessons[lessonIndex].sidebyside
	let paliTitle = lessonsData[chapterIndex].lessons[lessonIndex].paliname;
	let engTitle = lessonsData[chapterIndex].lessons[lessonIndex].engname;


</script>


<table>
<!-- 	<caption>Council budget (in £) 2018</caption> -->
    <thead>
        <tr>
            <th scope="col">{paliTitle}</th>
            <th scope="col">{engTitle}</th>
        </tr>
    </thead>
	<tbody>
		{#each sidebysideData as row}
		<tr>
			<td>{row.pali}</td>
			<td>{row.english}</td>
		</tr>
		{/each}
	</tbody>
	<tfoot>
		<tr>
			<td colspan="2">This PDF is part of an online Pāli course program offered free of charge by Pariyatti. To join a course please visit http://learning.pariyatti.org.
&copy;℗Pariyatti - www.pariyatti.org</td>
		</tr>
	</tfoot>
</table>



<style>
	table {
		border-collapse: collapse;
		box-sizing: border-box;
    text-indent: initial;
    border-spacing: 2px;
    border-color: grey;
		width: 100%;
    margin: .5rem 0 1rem;
	}

	td, th {
		padding: 1rem;
		border: 1px solid gray;
		font-size: 1.1rem
	}

	th {
		text-align: center;
		background: hsl(206, 51%, 84%);
    font-weight: 700;
	}

	tr:nth-child(even) {
		background: hsl(206, 51%, 95%);
	}

	tfoot td {
		font-size: .8rem
	}
</style>