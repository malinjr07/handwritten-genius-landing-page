<script lang="ts">
	import UnderlineSvg from '@svg/UnderlineSvg.svelte';
</script>

<section id="home-about" class="home-about">
	<div class="contentContainer">
		<!-- Header -->
		<header class="about-header">
			<h3>You Type</h3>
			<h2 class="hw-font uline-wrap">
				<span class="word">We</span>
				<span class="word">Write</span>
				<span class="underline">
					<UnderlineSvg class="underline-svg" />
				</span>
			</h2>
			<p>
				Handwrytten's handwritten note service allows you to scale your handwritten outreach,<br
					class="nobreak"
				/>
				creating positive impressions and long lasting bonds.
			</p>
		</header>

		<!-- Buckets - Split Layout -->
		<div class="buckets split">
			<!-- Left Bucket - You Type -->
			<div class="bucket left">
				<div class="bucket-content">
					<div class="bucket-visual">
						<!-- Placeholder for phone/typing animation visual -->
						<div class="visual-placeholder typing-visual"></div>
					</div>
					<div class="txt">
						<h3>You Type</h3>
						<p>
							Simply type your note, or use our AI to perfect your message. Then choose from our
							beautiful selection of cards. You can even design your own stationery!
						</p>
					</div>
				</div>
			</div>

			<!-- Right Bucket - We Write -->
			<div class="bucket right">
				<div class="bucket-content">
					<div class="bucket-visual">
						<!-- Placeholder for robot arms writing visual -->
						<div class="visual-placeholder writing-visual"></div>
					</div>
					<div class="txt">
						<h3>We Write</h3>
						<p>
							Handwrytten uses custom-designed handwriting robots that hold real pens to write out
							the notes in the handwriting style of your choice. Our AI ensures the note is
							completely unique and looks authentic.
						</p>
					</div>
				</div>
			</div>
		</div>

		<!-- Full Width Bucket - Stamped and Delivered -->
		<div class="buckets full">
			<div class="bucket-full-content">
				<div class="background">
					<img
						src="/about3-base@2x.png.webp"
						class="spacer"
						width="833"
						height="777"
						alt="delivery illustration"
					/>
				</div>
				<div class="txt">
					<div class="icon-stamp">
						<!-- Stamp icon placeholder -->
						<svg viewBox="0 0 80 80" fill="none" xmlns="http://www.w3.org/2000/svg">
							<circle cx="40" cy="40" r="38" stroke="#020f14" stroke-width="2" />
							<text
								x="40"
								y="45"
								text-anchor="middle"
								font-size="12"
								font-family="mrs-eaves-xl-serif, serif"
								fill="#020f14"
							>
								STAMP
							</text>
						</svg>
					</div>
					<h3>Stamped and delivered for you!</h3>
					<p>
						We send all notes via First Class postage. Domestic postage and delivery in the US and
						Canada. We also deliver to 190 other countries. Sending real cards online has never been
						easier!
					</p>
					<a href="/features" class="cta-btn orange">More Features</a>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	/* About Section Base */
	.home-about {
		padding-top: 100px;
		padding-bottom: 100px;
		background-color: #fff;
		position: relative;
	}

	/* Header */
	.about-header {
		text-align: center;
		margin-bottom: 80px;
	}

	.about-header h3 {
		font:
			400 24px/1.375 mrs-eaves-xl-serif,
			serif;
		color: #020f14;
		margin-bottom: 10px;
	}

	.about-header h2 {
		font:
			400 68px/1.12 hwryanregular,
			cursive;
		color: #020f14;
		margin-bottom: 30px;
		position: relative;
		display: inline-block;
	}

	.about-header h2 .word {
		display: inline-block;
		margin: 0 10px;
	}

	.about-header .uline-wrap {
		position: relative;
	}

	.about-header .underline {
		position: absolute;
		left: 50%;
		bottom: -10px;
		transform: translateX(-50%);
		width: 120px;
		height: 8px;
	}

	.about-header .underline :global(.underline-svg) {
		width: 100%;
		height: 100%;
	}

	.about-header p {
		font-size: 21px;
		line-height: 1.9;
		color: #020f14;
		max-width: 800px;
		margin: 0 auto;
	}

	.about-header .nobreak {
		display: none;
	}

	@media screen and (min-width: 1024px) {
		.about-header .nobreak {
			display: inline;
		}
	}

	/* Buckets - Split Layout */
	.buckets.split {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		gap: 40px;
		margin-bottom: 80px;
	}

	.bucket {
		flex: 1;
		min-width: 280px;
		max-width: 530px;
	}

	.bucket-content {
		position: relative;
	}

	.bucket-visual {
		margin-bottom: 30px;
	}

	.visual-placeholder {
		width: 100%;
		height: 400px;
		background-color: #f5f6f0;
		border-radius: 8px;
		position: relative;
	}

	.typing-visual::after {
		content: '';
		position: absolute;
		width: 60%;
		height: 80%;
		left: 20%;
		top: 10%;
		background: linear-gradient(135deg, #e8e9e4 0%, #d4d5d0 100%);
		border-radius: 20px;
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.writing-visual::after {
		content: '';
		position: absolute;
		width: 80%;
		height: 60%;
		left: 10%;
		top: 20%;
		background: linear-gradient(135deg, #fafaf7 0%, #f0f1ec 100%);
		border-radius: 4px;
		box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
	}

	.bucket .txt h3 {
		font:
			400 24px/1.375 mrs-eaves-xl-serif,
			serif;
		color: #020f14;
		margin-bottom: 16px;
	}

	.bucket .txt p {
		font-size: 18px;
		line-height: 1.9;
		color: #020f14;
	}

	/* Full Width Bucket */
	.buckets.full {
		position: relative;
	}

	.bucket-full-content {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: center;
		gap: 60px;
		background-color: #020f14;
		border-radius: 8px;
		padding: 60px;
		position: relative;
		overflow: hidden;
	}

	.bucket-full-content .background {
		flex: 1;
		min-width: 300px;
		max-width: 500px;
	}

	.bucket-full-content .background img {
		width: 100%;
		height: auto;
		opacity: 0.9;
	}

	.bucket-full-content .txt {
		flex: 1;
		min-width: 280px;
		max-width: 450px;
		text-align: center;
	}

	.bucket-full-content .icon-stamp {
		width: 80px;
		height: 80px;
		margin: 0 auto 20px;
	}

	.bucket-full-content .icon-stamp svg {
		width: 100%;
		height: 100%;
	}

	.bucket-full-content .icon-stamp svg circle {
		stroke: #fff;
	}

	.bucket-full-content .icon-stamp svg text {
		fill: #fff;
	}

	.bucket-full-content h3 {
		font:
			400 32px/1.375 mrs-eaves-xl-serif,
			serif;
		color: #fff;
		margin-bottom: 20px;
	}

	.bucket-full-content p {
		font-size: 18px;
		line-height: 1.9;
		color: rgba(255, 255, 255, 0.85);
		margin-bottom: 30px;
	}

	.bucket-full-content .cta-btn {
		display: inline-block;
	}

	/* Responsive */
	@media screen and (max-width: 900px) {
		.home-about {
			padding-top: 60px;
			padding-bottom: 60px;
		}

		.about-header {
			margin-bottom: 50px;
		}

		.about-header h2 {
			font-size: 52px;
		}

		.about-header p {
			font-size: 18px;
		}

		.buckets.split {
			flex-direction: column;
			align-items: center;
			gap: 50px;
		}

		.bucket {
			max-width: 100%;
		}

		.visual-placeholder {
			height: 300px;
		}

		.bucket-full-content {
			padding: 40px 30px;
			flex-direction: column;
		}
	}

	@media screen and (max-width: 640px) {
		.about-header h2 {
			font-size: 42px;
		}

		.about-header h3 {
			font-size: 20px;
		}

		.about-header p {
			font-size: 16px;
		}

		.bucket .txt h3 {
			font-size: 20px;
		}

		.bucket .txt p {
			font-size: 16px;
		}

		.bucket-full-content h3 {
			font-size: 26px;
		}

		.bucket-full-content p {
			font-size: 16px;
		}

		.visual-placeholder {
			height: 250px;
		}
	}
</style>
