<script>
	import RichPresence from '../molecules/RichPresence.svelte';
	import Tooltip from '../atoms/Tooltip.svelte';

	// i didnt write this idk
	let getAge = () => {
		let birthDate = new Date('2007/11/24');
		const ageMs = Date.now() - birthDate.getTime();
		const preciseAge = (ageMs / 31536000000).toFixed(10);
		return preciseAge;
	};

	let age = getAge();
	setInterval(() => {
		age = getAge();
	}, 1000);
</script>

<section id="about" class="wrapper">
	<div>
		<RichPresence />
	</div>
	<div class="text">
		<h2>bio</h2>
		<p>
			Hey there, I'm Vik! :] I'm a <Tooltip tip={age}
				><span>{Math.floor(Number(age))}</span></Tooltip
			>
			year old Programmer based in Germany🏛️. I’ve taken programming seriously since
			<span>2019</span>, and have been doodling little Projects since <span>2020</span>.
			However, sadly most of my Work is Private, so i cant show it to you :[. I like to use Git with in my oppinion the best Git Client 
			<Tooltip tip="🤓">
				<a href="https://github.com/real-airbauer" target="_blank" rel="noreferrer">
					<span>GitHub</span>
				</a>
			</Tooltip>
			. The Language that have my heart is <Tooltip tip="🔝">
				<a href="https://js.org/" target="_blank" rel="noreferrer">
					<span>JS</span>
				</a>
			</Tooltip>.
			
		</p>
	</div>
</section>

<style lang="scss">
	@import '../../styles/mixins.scss';

	section {
		margin-bottom: 6rem;
		display: grid;
		gap: 4.5rem;
		grid-template-columns: 1fr 1fr;
		align-items: center;
	}

	.text {
		position: relative;
		line-height: 1.75rem;
	}

	span {
		font-weight: 400;
		font-family: var(--font-two);
		font-size: 0.9rem;
		background-color: var(--neutral-one);
		border-radius: 7px;
		color: var(--yellow);
		padding: 0.2rem 0.5rem 0.2rem;
		width: fit-content;
	}

	a {
		text-decoration: none;
	}

	.text::before {
		@include outlineText($content: 'airbauer', $translateX: 97%, $translateY: -5%, $fontSize: 300px, $opacity: 0.22);
	}

	h2 {
		display: none;
		margin-top: 1rem;
	}

	@media (max-width: 868px) {
		section {
			display: flex;
			flex-direction: column;
			align-items: normal;
		}

		h2 {
			display: block;
			margin-bottom: 1rem;
		}
	}
</style>
