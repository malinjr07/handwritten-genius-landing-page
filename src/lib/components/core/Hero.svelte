<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import UnderlineSvg from '@svg/UnderlineSvg.svelte';
	import PlaneSvg from '@svg/PlaneSvg.svelte';
	import RobotHandSvg from '@svg/RobotHandSvg.svelte';

	let heroSection: HTMLElement;
	let robotHandEl: HTMLElement;
	let underlineEl: HTMLElement;
	let planeEl: HTMLElement;

	onMount(() => {
		// Animate underline drawing in
		gsap.fromTo(
			underlineEl,
			{ width: '0%', opacity: 0 },
			{ width: '100%', opacity: 1, duration: 1, delay: 0.5, ease: 'power2.out' }
		);

		// Animate robot hand sliding in
		gsap.fromTo(
			robotHandEl,
			{ x: -50, opacity: 0 },
			{ x: 0, opacity: 1, duration: 0.8, delay: 0.3, ease: 'power3.out' }
		);

		// Animate plane flying in
		gsap.fromTo(
			planeEl,
			{ x: 100, y: -50, opacity: 0, rotation: -20 },
			{ x: 0, y: 0, opacity: 1, rotation: 0, duration: 1.2, delay: 0.8, ease: 'power2.out' }
		);
	});
</script>

<section
	bind:this={heroSection}
	id="home-hero"
	class="relative min-h-screen overflow-hidden bg-gradient-to-b from-amber-50 to-white pt-32 pb-20 lg:pt-40 lg:pb-32"
>
	<div class="container mx-auto px-6 lg:px-18">
		<div class="grid lg:grid-cols-2 gap-12 items-center">
			<!-- Left Content -->
			<div class="text-center lg:text-left">
				<h1 class="text-4xl md:text-5xl lg:text-6xl font-bold text-gray-900 leading-tight mb-6">
					Your words.<br />
					In pen <span class="font-handwriting text-theme-1">+</span> ink.
				</h1>

				<a
					href="https://app.handwrytten.com/cards?login=true"
					target="_blank"
					rel="noopener noreferrer"
					class="inline-block px-8 py-4 bg-orange-500 hover:bg-orange-600 text-white font-bold text-lg rounded-lg shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-0.5"
				>
					Start Writing
				</a>

				<div class="mt-12">
					<p class="text-xl md:text-2xl text-gray-700 leading-relaxed">
						Handwritten. AI-powered.<br />
						Connections at
						<span class="relative inline-block">
							<span class="relative z-10 font-semibold">Scale!</span>
							<span
								bind:this={underlineEl}
								class="absolute bottom-0 left-0 h-2 w-full overflow-hidden"
							>
								<UnderlineSvg class="w-full h-full" />
							</span>
						</span>
					</p>
				</div>
			</div>

			<!-- Right Content - Robot Arm Animation -->
			<div class="relative flex justify-center lg:justify-end">
				<div class="relative w-full max-w-md">
					<!-- Robot Hand -->
					<div bind:this={robotHandEl} class="relative z-10">
						<RobotHandSvg class="w-full h-auto transform -rotate-12" />
						<div
							class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-4 h-4 bg-theme-1 rounded-full animate-pulse"
						></div>
					</div>

					<!-- Decorative Plane -->
					<div bind:this={planeEl} class="absolute -top-8 -right-8 w-16 h-16">
						<PlaneSvg class="w-full h-full" />
					</div>

					<!-- Decorative dotted lines -->
					<svg
						class="absolute inset-0 w-full h-full pointer-events-none opacity-30"
						viewBox="0 0 400 300"
					>
						<path
							d="M50,150 Q200,50 350,150"
							stroke="#020F14"
							stroke-width="2"
							stroke-dasharray="8,8"
							fill="none"
						/>
						<path
							d="M0,200 Q150,100 300,250"
							stroke="#020F14"
							stroke-width="1.5"
							stroke-dasharray="6,6"
							fill="none"
						/>
					</svg>
				</div>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div
		class="absolute bottom-0 left-0 w-full h-32 bg-gradient-to-t from-white to-transparent"
	></div>

	<!-- Animated floating elements -->
	<div
		class="absolute top-20 left-10 w-3 h-3 bg-orange-300 rounded-full animate-bounce opacity-60"
	></div>
	<div
		class="absolute top-40 right-20 w-2 h-2 bg-amber-400 rounded-full animate-ping opacity-40"
	></div>
	<div
		class="absolute bottom-40 left-1/4 w-4 h-4 bg-orange-200 rounded-full animate-pulse opacity-50"
	></div>
</section>

<style>
	.font-handwriting {
		font-family: 'Caveat', 'Brush Script MT', cursive;
	}

	@keyframes float {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-10px);
		}
	}
</style>
