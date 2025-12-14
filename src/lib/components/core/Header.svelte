<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';

	let isSticky = $state(false);
	let openDropdown = $state<string | null>(null);
	let openSubDropdown = $state<string | null>(null);
	let isMobileMenuOpen = $state(false);

	// Scroll handling for sticky header
	onMount(() => {
		const handleScroll = () => {
			isSticky = window.scrollY > 0;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	// Hover handlers for dropdowns (desktop only)
	function handleDropdownEnter(dropdownId: string, element: HTMLElement) {
		openDropdown = dropdownId;
		const subnav = element.querySelector('.subnav') as HTMLElement;
		if (subnav) {
			gsap.killTweensOf(subnav);
			subnav.style.display = 'block';
			gsap.to(subnav, {
				opacity: 1,
				y: 0,
				duration: 0.75,
				ease: 'elastic.out(3, 4)'
			});
		}
	}

	function handleDropdownLeave(element: HTMLElement) {
		openDropdown = null;
		openSubDropdown = null;
		const subnav = element.querySelector('.subnav') as HTMLElement;
		if (subnav) {
			gsap.killTweensOf(subnav);
			gsap.to(subnav, {
				opacity: 0,
				y: -10,
				duration: 0.5,
				ease: 'power3.inOut',
				onComplete: () => {
					subnav.style.display = 'none';
				}
			});
		}
	}

	// Sub-dropdown hover handlers
	function handleSubDropdownEnter(subId: string, element: HTMLElement) {
		openSubDropdown = subId;
		const subsubnav = element.querySelector('.subsubnav') as HTMLElement;
		if (subsubnav) {
			gsap.killTweensOf(subsubnav);
			subsubnav.style.display = 'block';
			gsap.to(subsubnav, {
				opacity: 1,
				y: 0,
				duration: 0.75,
				ease: 'elastic.out(3, 4)'
			});
		}
	}

	function handleSubDropdownLeave(element: HTMLElement) {
		openSubDropdown = null;
		const subsubnav = element.querySelector('.subsubnav') as HTMLElement;
		if (subsubnav) {
			gsap.killTweensOf(subsubnav);
			gsap.to(subsubnav, {
				opacity: 0,
				y: -10,
				duration: 0.5,
				ease: 'power3.inOut',
				onComplete: () => {
					subsubnav.style.display = 'none';
				}
			});
		}
	}

	function toggleMobileMenu() {
		isMobileMenuOpen = !isMobileMenuOpen;
	}
</script>

<header
	id="globalHeader"
	class="fixed top-0 left-0 w-full z-20 text-center overflow-visible transition-all duration-500"
	class:sticky={isSticky}
>
	<!-- Sticky Bar (white background with shadow) -->
	<div
		class="sticky-bar absolute left-0 top-0 w-full h-20 z-0 bg-white border-b border-black/10 transition-transform duration-500"
		class:translate-y-0={isSticky}
		class:-translate-y-full={!isSticky}
	></div>

	<!-- Logo Desktop -->
	<div
		class="logo-dsk absolute left-18 top-14 w-44 z-0 transition-all duration-300"
		class:opacity-0={isSticky}
		class:-translate-y-10={isSticky}
	>
		<a href="/" title="Handwrytten | Handwritten Notes Service and Card Automation">
			<img src="/logo@2x.png.webp" alt="Handwrytten" class="w-full h-auto" />
		</a>
	</div>

	<!-- Logo Sticky (animated logo for sticky state) -->
	<div
		class="logo-stk absolute left-18 top-4 w-14 z-0 transition-all duration-500"
		class:opacity-100={isSticky}
		class:translate-y-0={isSticky}
		class:opacity-0={!isSticky}
		class:-translate-y-20={!isSticky}
	>
		<a href="/" class="flex items-center" title="Handwrytten">
			<div class="logo-dot absolute left-0 top-0 w-14 h-14">
				<img src="/logo-dot.svg" alt="Handwrytten" class="w-full h-full" />
			</div>
			<svg class="logo-h1 absolute" style="width: 5px; height: 29px; left: 20px; top: 12px;">
				<defs>
					<mask id="h1-masker">
						<rect class="h1-rect" x="0" y="0" width="6" height="29" fill="#fff"></rect>
					</mask>
				</defs>
				<g mask="url(#h1-masker)">
					<image href="/logo-h1.svg" width="6" height="29"></image>
				</g>
			</svg>
			<svg class="logo-h2 absolute" style="width: 16px; height: 17px; left: 24px; top: 24px;">
				<defs>
					<mask id="h2-masker">
						<rect class="h2-rect" x="0" y="0" width="16" height="17" fill="#fff"></rect>
					</mask>
				</defs>
				<g mask="url(#h2-masker)">
					<image href="/logo-h2.svg" width="16" height="17"></image>
				</g>
			</svg>
		</a>
	</div>

	<!-- Top Navigation Links -->
	<nav
		class="toplinks hidden lg:inline-block pt-18 relative transition-all duration-500"
		class:-translate-y-10={isSticky}
	>
		<ul class="top flex items-center">
			<!-- Business Dropdown -->
			<li
				class="hasSub relative inline-block align-top"
				onmouseenter={(e) => handleDropdownEnter('business', e.currentTarget)}
				onmouseleave={(e) => handleDropdownLeave(e.currentTarget)}
			>
				<a
					href="/business"
					class="block relative text-sm text-gray-900 hover:text-theme-1 transition-colors z-2"
					title="Business"
				>
					Business
					<span class="icon-chevron-down text-xs ml-1 inline-block transition-colors">▼</span>
				</a>
				<nav
					class="subnav absolute left-0 top-0 pt-9 w-64 opacity-0 hidden origin-top"
					style="transform: translateY(-10px);"
				>
					<div class="relative">
						<ul class="border-3 border-gray-900 text-left bg-white relative">
							<li class="block relative">
								<a
									href="/business"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Business Overview</a
								>
							</li>
							<li
								class="hasSubSub block relative border-t border-black/20"
								onmouseenter={(e) => handleSubDropdownEnter('market', e.currentTarget)}
								onmouseleave={(e) => handleSubDropdownLeave(e.currentTarget)}
							>
								<a
									href="/market-solutions"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
								>
									Market Solutions
									<span class="icon-chevron-right absolute right-4 top-5 text-sm">▶</span>
								</a>
								<nav
									class="subsubnav absolute left-62 -top-0.5 w-64 opacity-0 hidden origin-top"
									style="transform: translateY(-10px);"
								>
									<ul class="border-3 border-gray-900 text-left bg-white">
										<li class="block">
											<a
												href="/automotive"
												class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
												>Automotive Dealerships</a
											>
										</li>
										<li class="block border-t border-black/20">
											<a
												href="/insurance"
												class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
												>Insurance Agents</a
											>
										</li>
										<li class="block border-t border-black/20">
											<a
												href="/nonprofit"
												class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
												>Nonprofit Organizations</a
											>
										</li>
										<li class="block border-t border-black/20">
											<a
												href="/real-estate"
												class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
												>Real Estate and Mortgage</a
											>
										</li>
										<li class="block border-t border-black/20">
											<a
												href="/retail"
												class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
												>Retail and eCommerce</a
											>
										</li>
									</ul>
								</nav>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/book-demo"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Book a Demo</a
								>
							</li>
						</ul>
					</div>
				</nav>
			</li>

			<!-- Features -->
			<li class="relative inline-block align-top ml-10">
				<a
					href="/features"
					class="block relative text-sm text-gray-900 hover:text-theme-1 transition-colors"
					title="Features">Features</a
				>
			</li>

			<!-- Integrations Dropdown -->
			<li
				class="hasSub relative inline-block align-top ml-10"
				onmouseenter={(e) => handleDropdownEnter('integrations', e.currentTarget)}
				onmouseleave={(e) => handleDropdownLeave(e.currentTarget)}
			>
				<a
					href="/integrations"
					class="block relative text-sm text-gray-900 hover:text-theme-1 transition-colors z-2"
					title="Integrations"
				>
					Integrations
					<span class="icon-chevron-down text-xs ml-1 inline-block transition-colors">▼</span>
				</a>
				<nav
					class="subnav absolute left-0 top-0 pt-9 w-64 opacity-0 hidden origin-top"
					style="transform: translateY(-10px);"
				>
					<div class="relative">
						<ul class="border-3 border-gray-900 text-left bg-white relative">
							<li class="block relative">
								<a
									href="/integrations"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Integrate & Automate</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/zapier"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Zapier</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/salesforce"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Salesforce</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/hubspot"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>HubSpot</a
								>
							</li>
						</ul>
					</div>
				</nav>
			</li>

			<!-- Pricing -->
			<li class="relative inline-block align-top ml-10">
				<a
					href="/pricing"
					class="block relative text-sm text-gray-900 hover:text-theme-1 transition-colors"
					title="Pricing">Pricing</a
				>
			</li>

			<!-- Resources Dropdown -->
			<li
				class="hasSub relative inline-block align-top ml-10"
				onmouseenter={(e) => handleDropdownEnter('resources', e.currentTarget)}
				onmouseleave={(e) => handleDropdownLeave(e.currentTarget)}
			>
				<a
					href="/resources"
					class="block relative text-sm text-gray-900 hover:text-theme-1 transition-colors z-2"
					title="Resources"
				>
					Resources
					<span class="icon-chevron-down text-xs ml-1 inline-block transition-colors">▼</span>
				</a>
				<nav
					class="subnav absolute left-0 top-0 pt-9 w-64 opacity-0 hidden origin-top"
					style="transform: translateY(-10px);"
				>
					<div class="relative">
						<ul class="border-3 border-gray-900 text-left bg-white relative">
							<li class="block relative">
								<a
									href="/blog"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors">Blog</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/tutorials"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Tutorials</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/faq"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors">FAQ</a
								>
							</li>
						</ul>
					</div>
				</nav>
			</li>

			<!-- About Dropdown -->
			<li
				class="hasSub relative inline-block align-top ml-10"
				onmouseenter={(e) => handleDropdownEnter('about', e.currentTarget)}
				onmouseleave={(e) => handleDropdownLeave(e.currentTarget)}
			>
				<a
					href="/about"
					class="block relative text-sm text-gray-900 hover:text-theme-1 transition-colors z-2"
					title="About"
				>
					About
					<span class="icon-chevron-down text-xs ml-1 inline-block transition-colors">▼</span>
				</a>
				<nav
					class="subnav absolute left-0 top-0 pt-9 w-64 opacity-0 hidden origin-top"
					style="transform: translateY(-10px);"
				>
					<div class="relative">
						<ul class="border-3 border-gray-900 text-left bg-white relative">
							<li class="block relative">
								<a
									href="/about"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>The Company</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/team"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Our Team</a
								>
							</li>
							<li class="block relative border-t border-black/20">
								<a
									href="/careers"
									class="block py-4 px-5 text-gray-900 hover:text-theme-1 transition-colors"
									>Careers</a
								>
							</li>
						</ul>
					</div>
				</nav>
			</li>
		</ul>
	</nav>

	<!-- CTA Items (Sign In / Sign Up) -->
	<div
		class="cta-items hidden lg:block absolute top-14 right-18 text-right transition-all duration-500"
		class:-translate-y-10={isSticky}
	>
		<ul class="flex items-center">
			<li class="inline-block align-middle">
				<a href="/signin" class="block text-sm text-gray-900 hover:text-theme-1 transition-colors"
					>Sign In</a
				>
			</li>
			<li class="inline-block align-middle ml-8">
				<a
					href="/signup"
					class="cta-btn inline-block px-6 py-3 bg-theme-1 text-white text-sm font-bold rounded hover:bg-theme-1/90 transition-colors"
					>Sign Up</a
				>
			</li>
		</ul>
	</div>

	<!-- Mobile Menu Button -->
	<button
		class="menu-btn lg:hidden absolute right-6 top-6 z-10 text-gray-900"
		onclick={toggleMobileMenu}
		aria-label="Toggle menu"
	>
		<svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
			<path
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				d="M4 6h16M4 12h16M4 18h16"
			></path>
		</svg>
	</button>
</header>

<!-- Mobile Menu -->
<div
	id="globalMenu"
	class="lg:hidden fixed top-0 left-0 w-full h-full bg-white z-40 transition-transform duration-500"
	class:translate-x-0={isMobileMenuOpen}
	class:translate-x-full={!isMobileMenuOpen}
>
	<div class="p-6">
		<button
			class="absolute top-6 right-6 text-gray-900"
			onclick={toggleMobileMenu}
			aria-label="Close menu"
		>
			<svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M6 18L18 6M6 6l12 12"
				></path>
			</svg>
		</button>
		<nav class="mt-16">
			<ul class="space-y-4">
				<li>
					<a href="/business" class="block text-lg text-gray-900 hover:text-theme-1">Business</a>
				</li>
				<li>
					<a href="/features" class="block text-lg text-gray-900 hover:text-theme-1">Features</a>
				</li>
				<li>
					<a href="/integrations" class="block text-lg text-gray-900 hover:text-theme-1"
						>Integrations</a
					>
				</li>
				<li>
					<a href="/pricing" class="block text-lg text-gray-900 hover:text-theme-1">Pricing</a>
				</li>
				<li>
					<a href="/resources" class="block text-lg text-gray-900 hover:text-theme-1">Resources</a>
				</li>
				<li><a href="/about" class="block text-lg text-gray-900 hover:text-theme-1">About</a></li>
				<li class="pt-4 border-t border-gray-200">
					<a href="/signin" class="block text-lg text-gray-900 hover:text-theme-1">Sign In</a>
				</li>
				<li>
					<a
						href="/signup"
						class="inline-block px-6 py-3 bg-theme-1 text-white font-bold rounded hover:bg-theme-1/90"
						>Sign Up</a
					>
				</li>
			</ul>
		</nav>
	</div>
</div>
