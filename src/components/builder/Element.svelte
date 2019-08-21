<script>
	export let builderId, tag, id, classes, content, appHover, appFocus;

	let curHover, curFocus;

	appHover.subscribe(value => {
		curHover = value;
	});

	appFocus.subscribe(value => {
		curFocus = value;
	});
</script>

{#if tag == 'div'}
	<div id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</div>
{:else if tag == 'h1'}
	<h1 id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</h1>
{:else if tag == 'h2'}
	<h2 id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</h2>
{:else if tag == 'h3'}
	<h3 id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</h3>
{:else if tag == 'h4'}
	<h4 id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</h4>
{:else if tag == 'h5'}
	<h5 id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</h5>
{:else if tag == 'h6'}
	<h6 id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</h6>
{:else if tag == 'a'}
	<a id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</a>
{:else if tag == 'span'}
	<span id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</span>
{:else if tag == 'p'}
	<p id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</p>
{:else if tag == 'ul'}
	<ul id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</ul>
{:else if tag == 'ol'}
	<ol id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</ol>
{:else if tag == 'li'}
	<li id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</li>
{:else if tag == 'nav'}
	<nav id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</nav>
{:else if tag == 'header'}
	<header id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</header>	
{:else if tag == 'main'}
	<main id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</main>
{:else if tag == 'aside'}
	<aside id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</aside>
{:else if tag == 'footer'}
	<footer id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</footer>
{:else if tag == 'table'}
	<table id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</table>
{:else if tag == 'thead'}
	<thead id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</thead>
{:else if tag == 'tbody'}
	<tbody id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</tbody>
{:else if tag == 'tfoot'}
	<tfoot id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</tfoot>
{:else if tag == 'tr'}
	<tr id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</tr>
{:else if tag == 'td'}
	<td id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</td>
{:else if tag == 'br'}
	<br id={id} class:active={builderId == curHover || builderId == curFocus} class={classes} />
{:else if tag == 'hr'}
	<hr id={id} class:active={builderId == curHover || builderId == curFocus} class={classes} />
{:else if tag == 'i'}
	<i id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</i>
{:else if tag == 'b'}
	<b id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</b>
{:else if tag == 'strong'}
	<strong id={id} class:active={builderId == curHover || builderId == curFocus} class={classes}>{@html content}</strong>
{/if}