<script lang="ts">
	import CardsSvg from '@svg/CardsSvg.svelte';
</script>

<section id="home-cards" class="home-cards">
	<!-- Curved shape background -->
	<div class="shape-bg-wrap">
		<div class="shape-wrap">
			<div class="shape-bg"></div>
		</div>
	</div>

	<div class="contentContainer">
		<div class="col right">
			<h2>
				Choose from our<br />
				cards <span class="hw-font">or</span> design<br />
				your own.
				<span class="dots">
					<svg width="24" height="24" viewBox="0 0 24 24" fill="none">
						<circle cx="4" cy="12" r="3" fill="#020f14" />
						<circle cx="12" cy="12" r="3" fill="#020f14" />
						<circle cx="20" cy="12" r="3" fill="#020f14" />
					</svg>
				</span>
			</h2>
			<p>
				Over 100 designs to choose from or design your own. Our online card customizer makes it
				simple. All cards are printed on thick, luxurious stock. Feeling picky? We can print custom
				cards to your exacting specifications.
			</p>

			<a
				href="https://app.handwrytten.com/cards"
				target="_blank"
				rel="noopener noreferrer"
				class="cta-btn orange"
			>
				Our Cards
			</a>
		</div>
	</div>

	<!-- Cards Visual Background -->
	<div class="bg-wrap cards-visual">
		<div class="cards-stack">
			<div class="card-item" data-num="1">
				<CardsSvg class="card-svg" />
			</div>
			<div class="card-item" data-num="2">
				<CardsSvg class="card-svg" />
			</div>
			<div class="card-item" data-num="3">
				<CardsSvg class="card-svg" />
			</div>
		</div>
	</div>
</section>

<style>
	/* Cards Section Base */
	.home-cards {
		padding-top: 120px;
		padding-bottom: 180px;
		background-color: #fff;
		position: relative;
		overflow: hidden;
	}

	/* Shape Background */
	.shape-bg-wrap {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		overflow: hidden;
	}

	.shape-wrap {
		position: absolute;
		left: 50%;
		top: 0;
		transform: translateX(-50%);
		width: 100%;
		min-width: 1830px;
		height: 100%;
	}

	.shape-bg {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 730px;
		background-color: #f5f6f0;
		clip-path: ellipse(100% 80% at 50% 0%);
	}

	/* Content */
	.home-cards .contentContainer {
		position: relative;
		z-index: 2;
		display: flex;
		justify-content: flex-end;
	}

	.home-cards .col.right {
		width: 100%;
		max-width: 540px;
		text-align: left;
	}

	.home-cards h2 {
		font:
			400 68px/1.12 mrs-eaves-xl-serif,
			serif;
		color: #020f14;
		margin-bottom: 30px;
	}

	.home-cards .hw-font {
		font-family: hwryanregular, cursive;
		font-size: 68px;
	}

	.home-cards .dots {
		display: inline-block;
		margin-left: 10px;
		vertical-align: middle;
	}

	.home-cards .dots svg {
		width: 60px;
		height: auto;
	}

	.home-cards p {
		font-size: 21px;
		line-height: 1.9;
		color: #020f14;
		margin-bottom: 40px;
	}

	/* Cards Visual */
	.bg-wrap.cards-visual {
		position: absolute;
		left: 0;
		top: 50%;
		transform: translateY(-50%);
		width: 50%;
		height: 100%;
		pointer-events: none;
	}

	.cards-stack {
		position: relative;
		width: 100%;
		height: 100%;
	}

	.card-item {
		position: absolute;
		width: 200px;
		transition: transform 0.3s ease;
	}

	.card-item :global(.card-svg) {
		width: 100%;
		height: auto;
		filter: drop-shadow(0 10px 30px rgba(0, 0, 0, 0.15));
	}

	.card-item[data-num='1'] {
		left: 10%;
		top: 20%;
		transform: rotate(-8deg);
	}

	.card-item[data-num='2'] {
		left: 25%;
		top: 35%;
		transform: rotate(5deg);
	}

	.card-item[data-num='3'] {
		left: 5%;
		top: 55%;
		transform: rotate(-3deg);
	}

	/* Responsive */
	@media screen and (max-width: 1200px) {
		.home-cards .col.right {
			max-width: 480px;
		}

		.home-cards h2 {
			font-size: 52px;
		}

		.home-cards .hw-font {
			font-size: 52px;
		}

		.card-item {
			width: 160px;
		}
	}

	@media screen and (max-width: 900px) {
		.home-cards {
			padding-top: 80px;
			padding-bottom: 120px;
		}

		.home-cards .contentContainer {
			justify-content: center;
		}

		.home-cards .col.right {
			text-align: center;
			max-width: 100%;
		}

		.home-cards h2 {
			font-size: 42px;
		}

		.home-cards .hw-font {
			font-size: 42px;
		}

		.home-cards p {
			font-size: 18px;
		}

		.home-cards .dots svg {
			width: 40px;
		}

		.bg-wrap.cards-visual {
			position: relative;
			width: 100%;
			height: 300px;
			transform: none;
			margin-top: 40px;
		}

		.cards-stack {
			display: flex;
			justify-content: center;
			align-items: center;
			gap: 20px;
		}

		.card-item {
			position: relative;
			width: 120px;
			left: auto !important;
			top: auto !important;
		}

		.card-item[data-num='1'] {
			transform: rotate(-5deg);
		}

		.card-item[data-num='2'] {
			transform: rotate(0deg) translateY(-20px);
		}

		.card-item[data-num='3'] {
			transform: rotate(5deg);
		}
	}

	@media screen and (max-width: 640px) {
		.home-cards h2 {
			font-size: 32px;
		}

		.home-cards .hw-font {
			font-size: 32px;
		}

		.home-cards p {
			font-size: 16px;
		}

		.card-item {
			width: 100px;
		}

		.bg-wrap.cards-visual {
			height: 200px;
		}
	}
</style>
