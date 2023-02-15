<script>
	import CardList from "./cards.svelte";
	// import Card from "./lib/components/card.svelte";
	import Card from "./lib/components/card-proxy.svelte";
  import { onMount } from "svelte";

	let showcase, basics, reverse, holos, cosmos, amazings, radiant, basicGallery, 
			vee, veeUltra, veeAlt, veeMax, veeMaxAlt, veeStar, 
			trainerHolo, rainbow, gold, veeGallery, shinyVault;

	let isLoading = true;

	const getCards = async () => {
		let promiseArray = [];

		let cardFetch = await fetch("/data/cards.json");
		let cards = await cardFetch.json();
		return cards;
	};

	const loadCards = async() => {
		return getCards()
			.then((cards) => {
				window.cards = cards;
				showcase = cards[0];
				basics = cards.slice(1, 4);
				reverse = [...cards.slice(4, 7), ...cards.slice(70,76)];
				holos = cards.slice(7, 13);
				cosmos = cards.slice(13, 16);
				amazings = cards.slice(76, 85);
				radiant = cards.slice(16, 19);
				basicGallery = cards.slice(19, 22);
				vee = cards.slice(22, 25);
				veeUltra = cards.slice(25, 28);
				veeAlt = cards.slice(28, 34);
				veeMax = cards.slice(37, 40);
				veeMaxAlt = cards.slice(40, 43);
				veeStar = cards.slice(43, 46);
				trainerHolo = cards.slice(46, 52);
				rainbow = cards.slice(52, 58);
				gold = cards.slice(58, 64);
				veeGallery = cards.slice(64, 70);
				shinyVault = cards.slice(85,91);
				isLoading = false;
			});
	};

	onMount(() => {
		loadCards();
		const $headings = document.querySelectorAll("h1,h2,h3");
		const $anchor = [...$headings].filter((el) => {
			const id = el.getAttribute("id")?.replace(/^.*?-/g,"");
			const hash = window.location.hash?.replace(/^.*?-/g,"")
			return id === hash;
		})[0];
		if( $anchor ) {
			setTimeout(() => {
				$anchor.scrollIntoView();
			},100);
		}
	});
</script>

<main>
	<header>
		<h1 id="⚓-top">JASARENOV <sup>V1</sup></h1>

		<p class="author">By <a href="https://instagram.com/anticopyright"><svg role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Adit</title><path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/></svg> @anticopyright</a> |
			<em><a href="https://anticopyright.my.id"><svg role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Anticoyright</title><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg> Adit Anticopyright</em>
		</p>

		<section class="intro" id="⚓-intro">
			<p>

				<mark>JASARENOV</mark> melayani mulai perbaikan <mark>TERKECIL</mark> apapun maupun Renovasi Rumah bahkan Bangun Rumah mulai Awal.
				
			</p>
			<br>
			<p>

				Didukung <mark>JASA TUKANG SPESIALIS</mark> sesuai bidang pengerjaan dengan harga yang kompetitif, <mark>HARGA DITENTUKAN SEBELUM PENGERJAAN</mark>. 
			
			</p>
		</section>

		<div class="showcase">
			{#if isLoading}
				loading...
			{:else}
				<Card
					id={showcase.id}
					name={showcase.name}
					set={showcase.set}
					number={showcase.number}
					types={showcase.types}
					supertype={showcase.supertype}
					subtypes={showcase.subtypes}
					rarity={showcase.rarity}
					showcase={true}
				/>
			{/if}
		</div>

		<section class="info">
			<h3><mark>SOLUSI MUDAH RENOVASI RUMAH ANDA!</mark></h3>

			<hr />

			<p class="small">
				Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
			</p>
		</section>
	</header>

	<h2 id="⚓-visi-misi">
		<a href="#⚓-visi-misi">
			Visi &amp; Misi
		</a>
	</h2>
	<p>
		<!-- All cards get a 3d rotation with CSS based on the cursor position.<br /> The default basic
		non-holo cards simply apply a <mark>flare/glare effect</mark> to the card which follows the mouse. -->

		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each basics as card, id}
				<Card
					id={card.id}
					name={card.name}
					img={card.images.large}
					number={card.number}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-keramik">
		<a href="#⚓-keramik">
			Pemasangan Lantai Keramik
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each reverse as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
					isReverse
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-rolling-door">
		<a href="#⚓-rolling-door">
			Rolling Door
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each holos as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-renovasi-rumah">
		<a href="#⚓-renovasi-rumah">
			Jasa Renovasi Rumah
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>
	<h3>Jasa Renovasi Rumah</h3>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each cosmos as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-atap-baja-ringan">
		<a href="#⚓-atap-baja-ringan">
			Atap Baja Ringan
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each amazings as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-modern-interior">
		<a href="#⚓-modern-interior">
			Modern Interior
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each radiant as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-intaslasi-listrik">
		<a href="#⚓-intaslasi-listrik">
			Instalasi Listrik
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each basicGallery as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-pemasangan-gypsum">
		<a href="#⚓-pemasangan-gypsum">
			Pemasangan Gypsum
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each vee as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-pengecetan-texture">
		<a href="#⚓-pengecetan-texture">
			Pokemon V <sup>(Full Art)</sup>
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>
	<p>
		The texture effect is not identical to reality as the real cards each have a unique pattern that
		follows the art.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each veeUltra as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-canopy">
		<a href="#⚓-canopy">
			Pemasangan <sup>CANOPY</sup>
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>
	<p>Canopy.</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each veeAlt as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>

	<h2 id="⚓-pemasangan-teraso">
		<a href="#⚓-pemasangan-teraso">
			VMax
		</a>
	</h2>
	<p>
		Lorem ipsum dolor sit amet, <mark>consectetur adipiscing elit</mark>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	</p>

	<CardList>
		{#if isLoading}
			loading...
		{:else}
			{#each veeMax as card, id}
				<Card
					id={card.id}
					name={card.name}
					number={card.number}
					set={card.set}
					types={card.types}
					supertype={card.supertype}
					subtypes={card.subtypes}
					rarity={card.rarity}
				/>
			{/each}
		{/if}
	</CardList>
</main>

<div class="back-to-top">
  <a href="#⚓-top">Back to Top</a>
</div>

<style>
  .back-to-top a {
    color: inherit;
    text-decoration: none;
  }
</style>
