<script>
	import { readable } from 'svelte/store';

	let months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

	const month = readable('', (set) => {
		setInterval(() => {
			set(months[new Date().getMonth()]);
		}, 1000);
	});

	const year = readable('', (set) => {
		setInterval(() => {
			set(new Date().getFullYear());
		}, 1000);
	});

	const day = readable('', (set) => {
		setInterval(() => {
			set(new Date().getDate());
		}, 1000);
	});

	const period = readable('', (set) => {
		setInterval(() => {
			set(new Date().getHours() < 12 ? 'AM' : 'PM');
		}, 1000);
	});

	const hour = readable('', (set) => {
		setInterval(() => {
			set(new Date().getHours());
		}, 1000);
	});

	const minutes = readable('', (set) => {
		setInterval(() => {
			set(new Date().getMinutes());
		}, 1000);
	});

	const seconds = readable('', (set) => {
		setInterval(() => {
			set(new Date().getSeconds());
		}, 1000);
	});
</script>

<main>
	<div class="container">
        <p><span style="color:#d50fd5">const</span> <span style="color: #00FF00;">clock</span> <span style="color: #FF4500;">=</span> <span id="rectangles">&#123;</span></p>
        <div class="content">
			<p id="hour">hour: <span id="numbers">{$hour}</span></p>
			<p id="minutes">minutes: <span id="numbers">{$minutes}</span></p>
			<p id="seconds">seconds: <span id="numbers">{$seconds}</span></p>
			<p id="period">period: <span id="str">"{$period}"</span></p>
			<p id="day">day: <span id="numbers">{$day}</span></p>
			<p id="month">month: <span id="str">"{$month}"</span></p>
			<p id="year">year: <span id="numbers">{$year}</span></p>
		</div>
		<p id="rectangles">&#125;</p>
	</div>
</main>

<style>
	main {
		position: absolute;
		background-color: #111111;
		width: 100%;
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.container {
		color: white;
	}

	.content {
		position: relative;
		display: flex;
		flex-direction: column;
		left: 1em;
	}

	p {
		font-size: 1.5em;
        font-weight: bold;
        letter-spacing: 1.2px;
        font-family: "Roboto", sans-serif;
		margin-block: 0.4em;
	}

    #rectangles {
        color: #00FFFF;
    }

    #numbers {
        color: orange;
    }

    #str {
        color: greenyellow;
    }

	@media only screen and (max-height: 700px){
		p {
			font-size: 1.2em;
		}
	}
</style>
