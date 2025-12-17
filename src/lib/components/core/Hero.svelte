<script lang="ts">
	import UnderlineSvg from '@svg/UnderlineSvg.svelte';
	import HeroArmSideSvg from '@svg/HeroArmSideSvg.svelte';
	import RobotHandSvg from '@svg/RobotHandSvg.svelte';
	import StretchArmSvg from '@svg/StretchArmSvg.svelte';
</script>

<section id="home-hero" class="home-hero">
	<div class="contentContainer">
		<h1>
			Your words.<br />
			In pen <span class="hw-font">+</span> ink.
		</h1>

		<a
			href="https://app.handwrytten.com/cards?login=true"
			target="_blank"
			rel="noopener noreferrer"
			class="cta-btn orange"
		>
			Start Writing
		</a>

		<div class="writer-wrap side">
			<p>
				Handwritten. AI-powered.<br />
				Connections at
				<span class="uline-wrap">
					<span class="txt">Scale!</span>
					<span class="underline">
						<UnderlineSvg class="underline-svg" />
					</span>
				</span>
			</p>

			<!-- Side Arm with Robot Hand -->
			<div class="side-arm part">
				<div class="inner">
					<HeroArmSideSvg class="arm-side-svg" />
					<div class="robot-hand part">
						<div class="hand-inner part">
							<RobotHandSvg class="hand-img" />
							<div class="ball"></div>
						</div>
						<div class="stretch-arm part">
							<StretchArmSvg class="stretch-arm-svg" />
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Background wrapper -->
	<div class="bg-wrap">
		<!-- Background layer 1 - dotted lines -->
		<div class="background cn" data-num="1">
			<div class="part dline dsk">
				<img
					src="/home-hero-dlines@2x.png.webp"
					width="1800"
					height="1069"
					alt="decorative lines"
				/>
			</div>
			<div class="part botpipe">
				<img src="/hero-botpipe@2x.png.webp" width="250" height="120" alt="pipe decoration" />
			</div>
		</div>

		<!-- Background layer 2 - photos -->
		<div class="background cn" data-num="2">
			<div class="photo-group">
				<div class="photo part" data-num="2">
					<img src="/home-hero-photo2@2x.png" width="568" height="469" alt="handwritten card" />
				</div>
				<div class="photo part" data-num="3">
					<img src="/home-hero-photo3@2x.png" width="573" height="503" alt="handwritten card" />
				</div>
				<div class="photo part" data-num="1">
					<img src="/home-hero-photo1@2x.png" width="640" height="690" alt="handwritten card" />
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	/* Hero Section Base */
	.home-hero {
		padding-top: 212px;
		padding-bottom: 433px;
		background-color: #f5f6f0;
		position: relative;
		overflow: visible;
	}

	.home-hero .contentContainer {
		position: relative;
		z-index: 2;
	}

	/* Typography */
	.home-hero h1 {
		font:
			400 68px/1.12 mrs-eaves-xl-serif,
			serif;
		color: #020f14;
		margin-bottom: 0;
	}

	.home-hero .hw-font {
		font-family: hwryanregular, cursive;
		font-size: 115px;
		display: inline-block;
		width: 35px;
		text-align: center;
		transform: translateY(5px);
	}

	.home-hero .cta-btn {
		margin: 27px 0;
	}

	/* Writer wrap section */
	.home-hero .writer-wrap {
		position: relative;
		margin-top: 30px;
	}

	.home-hero .writer-wrap p {
		font-size: 21px;
		line-height: 1.9;
		color: #020f14;
	}

	/* Underline effect */
	.home-hero .uline-wrap {
		position: relative;
		display: inline-block;
	}

	.home-hero .uline-wrap .txt {
		position: relative;
		z-index: 1;
	}

	.home-hero .uline-wrap .underline {
		position: absolute;
		left: 0;
		bottom: -2px;
		width: 54px;
		height: 6px;
		overflow: hidden;
	}

	.home-hero .uline-wrap .underline :global(.underline-svg) {
		position: absolute;
		left: 0;
		top: 0;
		width: 54px;
		height: 6px;
	}

	/* Side Arm */
	.home-hero .side-arm {
		position: absolute;
		left: -219px;
		top: 176px;
		width: 316px;
	}

	.home-hero .side-arm .inner {
		position: relative;
	}

	.home-hero .side-arm .inner > :global(.arm-side-svg) {
		width: 100%;
		height: auto;
	}

	/* Robot Hand */
	.home-hero .robot-hand {
		position: absolute;
		left: 252px;
		top: -45px;
		width: 108px;
		height: 45px;
	}

	.home-hero .robot-hand .hand-inner {
		position: absolute;
		bottom: 0;
		width: 100%;
		height: 100%;
		z-index: 1;
		transform: translateY(-24px);
	}

	.home-hero .robot-hand .hand-inner :global(.hand-img) {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: auto;
		transform: rotate(-14deg);
		transform-origin: bottom center;
	}

	.home-hero .robot-hand .hand-inner .ball {
		width: 12px;
		height: 12px;
		border-radius: 12px;
		background-color: #020f14;
		position: absolute;
		bottom: -4px;
		left: 50%;
		transform: translateX(-50%);
	}

	.home-hero .robot-hand .stretch-arm {
		position: absolute;
		width: 4px;
		height: 100px;
		left: 50%;
		margin-left: -2px;
		bottom: 0;
		transform-origin: bottom center;
		transform: scaleY(0.24);
	}

	.home-hero .robot-hand .stretch-arm :global(.stretch-arm-svg) {
		width: 100%;
		height: 100%;
		position: absolute;
		left: 0;
		top: 0;
	}

	/* Background wrapper */
	.home-hero .bg-wrap {
		position: absolute;
		left: 0;
		top: auto;
		bottom: -319px;
		width: 100%;
		height: 1168px;
		overflow: hidden;
	}

	.home-hero .background {
		position: absolute;
		left: 0;
		top: 0;
		z-index: 0;
	}

	.home-hero .background.cn {
		width: 1800px;
		left: 50%;
		margin-left: -900px;
	}

	/* Dotted lines background */
	.home-hero .background[data-num='1'] .dline.dsk {
		width: 100%;
	}

	.home-hero .background[data-num='1'] .dline.dsk img {
		width: 100%;
		height: auto;
		display: block;
	}

	.home-hero .background[data-num='1'] .botpipe {
		position: absolute;
		width: 250px;
		left: 297px;
		top: 728px;
	}

	.home-hero .background[data-num='1'] .botpipe img {
		width: 100%;
		height: auto;
	}

	/* Photo group */
	.home-hero .background[data-num='2'] {
		pointer-events: none;
	}

	.home-hero .background[data-num='2'] .photo-group {
		position: absolute;
		left: 50%;
		margin-left: -600px;
		width: 1200px;
		height: 1100px;
	}

	.home-hero .photo {
		position: absolute;
		left: 0;
		top: 0;
	}

	.home-hero .photo img {
		width: 100%;
		height: auto;
		display: block;
	}

	.home-hero .photo[data-num='1'] {
		width: 640px;
		left: 160px;
		top: 138px;
	}

	.home-hero .photo[data-num='2'] {
		width: 568px;
		left: 562px;
		top: 365px;
	}

	.home-hero .photo[data-num='3'] {
		width: 573px;
		left: 496px;
		top: 648px;
	}

	/* Part utility class */
	.part {
		position: absolute;
		left: 0;
		top: 0;
	}

	.part img {
		width: 100%;
		height: auto;
		display: block;
	}

	/* Tablet Responsive */
	@media screen and (max-width: 1024px) {
		.home-hero {
			padding-top: 160px;
			padding-bottom: 350px;
		}

		.home-hero h1 {
			font-size: 52px;
		}

		.home-hero .hw-font {
			font-size: 90px;
		}

		.home-hero .side-arm {
			display: none;
		}

		.home-hero .bg-wrap {
			bottom: -200px;
			height: 900px;
		}

		.home-hero .photo[data-num='1'] {
			width: 480px;
			left: 200px;
			top: 100px;
		}

		.home-hero .photo[data-num='2'] {
			width: 400px;
			left: 500px;
			top: 280px;
		}

		.home-hero .photo[data-num='3'] {
			width: 400px;
			left: 450px;
			top: 480px;
		}
	}

	/* Mobile Responsive */
	@media screen and (max-width: 768px) {
		.home-hero {
			padding-top: 140px;
			padding-bottom: 280px;
		}

		.home-hero h1 {
			font-size: 42px;
			text-align: center;
		}

		.home-hero .hw-font {
			font-size: 72px;
			width: 28px;
		}

		.home-hero .cta-btn {
			display: block;
			text-align: center;
			margin: 27px auto;
		}

		.home-hero .writer-wrap p {
			text-align: center;
			font-size: 18px;
		}

		.home-hero .bg-wrap {
			bottom: -150px;
			height: 700px;
		}

		.home-hero .photo[data-num='1'] {
			width: 320px;
			left: 50%;
			margin-left: -160px;
			top: 80px;
		}

		.home-hero .photo[data-num='2'] {
			width: 280px;
			left: 50%;
			margin-left: -50px;
			top: 250px;
		}

		.home-hero .photo[data-num='3'] {
			width: 280px;
			left: 50%;
			margin-left: -100px;
			top: 400px;
		}
	}

	/* Small Mobile */
	@media screen and (max-width: 480px) {
		.home-hero {
			padding-top: 120px;
			padding-bottom: 220px;
		}

		.home-hero h1 {
			font-size: 32px;
		}

		.home-hero .hw-font {
			font-size: 56px;
			width: 22px;
		}

		.home-hero .writer-wrap p {
			font-size: 16px;
		}

		.home-hero .bg-wrap {
			bottom: -100px;
			height: 500px;
		}

		.home-hero .photo[data-num='1'] {
			width: 240px;
			margin-left: -120px;
			top: 60px;
		}

		.home-hero .photo[data-num='2'] {
			width: 200px;
			margin-left: -30px;
			top: 180px;
		}

		.home-hero .photo[data-num='3'] {
			width: 200px;
			margin-left: -80px;
			top: 300px;
		}
	}
</style>
