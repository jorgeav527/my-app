<script>
    import Nested from './Nested.svelte';
    let name = 'Svelte';
    let src = "/src/lib/assets/me_background_gray.jpg";
    let string = `this string contains some <strong>HTML!!!</strong>`;
    let count = 0;
    let numbers = [1, 2, 3, 4];

    $: doubled = count * 2;
    // $: console.log(`Count after button press: ${count}`);
    
	function addNumber() {
		numbers.push(numbers.length + 1);
        numbers = numbers
	}
    $: sum = numbers.reduce((total, currentNumber) => total + currentNumber, 0);
    function increment() {
        count += 1;
    }
    // import { getRandomNumber } from './utils.js';

	// let promise = getRandomNumber();

	// function handleClick() {
	// 	promise = getRandomNumber();
	// }
    let m = { x: 0, y: 0 };

    /**
	 * @param {{ clientX: number; clientY: number; }} event
	 */
    function handleMove(event) {
        m.x = event.clientX;
        m.y = event.clientY;
    }
    import Inner from './Inner.svelte';

    /**
	 * @param {{ detail: { text: any; }; }} event
	 */
    function handleMessage(event) {
        alert(event.detail.text);
    }
    import { onMount } from 'svelte';
    import BigRedButtom from './BigRedButtom.svelte';
    import horn from '/src/lib/assets/horn.mp3';

    /**
	 * @type {HTMLAudioElement}
	 */
    let audio;

    onMount(() => {
        audio = new Audio(horn);
    });

    function tocar() {
        if (audio) {
            audio.load();
            audio.play();
        }
    }
    let questions = [
		{
			id: 1,
			text: `Where did you go to school?`
		},
		{
			id: 2,
			text: `What is your mother's name?`
		},
		{
			id: 3,
			text: `What is another personal fact that an attacker could easily find with Google?`
		}
	];
    /**
	 * @type {{ id: any; text: any; }}
	 */
    let selected;
    let answer = "";
    function manejoSubmit() {
        alert(
            `answered question ${selected.id} (${selected.text}) with "${answer}"`
        )
    }
</script>

<BigRedButtom on:click={tocar} />

<Inner on:message={handleMessage} />

<div on:pointermove={handleMove}>
	The pointer is at {m.x} x {m.y}
</div>
<h1>Hello {name.toUpperCase()}!</h1>

<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation Count {count} doubled {doubled}</p>
<img src={src} alt="me_background_gray">
<button on:click={() => alert('clicked')}>
	Click meeeeeeeeeeeeeeeeeeeeeeeees
</button>
<p>{@html string}</p>
<button on:click={increment}>
    Clicked {count}
    {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>

<p>{numbers.join(' + ')} = {sum}</p>
<button on:click={addNumber}>
	Add a number
</button>
<Nested answer={42} />
{#if count > 10}
	<p>{count} is greater than 10</p>
{/if}

<!-- <button on:click={handleClick}>
	generate random number
</button>

{#await promise}
	<p>...waiting</p>
{:then number}
	<p>The number is {number}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await} -->



<style>
    img {
      width: 100px;
      height: auto;
    }
    p {
		color: goldenrod;
		font-family: 'Comic Sans MS', cursive;
		font-size: 2em;
	}
    /* div {
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		padding: 1rem;
	} */
</style>
