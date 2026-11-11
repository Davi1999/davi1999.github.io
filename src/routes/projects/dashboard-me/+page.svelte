<script lang="ts">
	const version = '1.2.1';
	const releaseTag = `dashboard-me-v${version}`;
	const releaseBase = `https://github.com/Davi1999/davi1999.github.io/releases/download/${releaseTag}`;
	const releaseUrl = `https://github.com/Davi1999/davi1999.github.io/releases/tag/${releaseTag}`;

	const windowsInstaller = 'dashboard-me_1.2.1_x64-setup.exe';
	const macInstaller = 'dashboard-me_1.2.1_universal.dmg';

	const downloads = [
		{
			platform: 'Windows',
			label: 'Download for Windows',
			file: windowsInstaller,
			url: `${releaseBase}/${windowsInstaller}`,
			meta: 'Windows 10/11 64-bit · 3.9 MB',
			hash: '6df6b2545a09763ecf0e4a5ad757136429dd6e430832c75f13f2ccd28976be39',
			primary: true
		},
		{
			platform: 'macOS',
			label: 'Download for macOS',
			file: macInstaller,
			url: `${releaseBase}/${macInstaller}`,
			meta: 'macOS 11+ · Intel + Apple Silicon · 12.5 MB',
			hash: '4156ec0a307ccae9738619385a09bc37102361191d6e20d87d45c2ec1c4ec269',
			primary: false,
			beta: true
		}
	];

	const features = [
		'Weather with hourly and daily forecasts, powered by Open-Meteo',
		'Now Playing with Windows media session artwork and playback controls',
		'Football scores and league tables through SportScore or 5DollarFootballAPI',
		'World Clock for any city, Quick Links, and app shortcuts with real app icons',
		'An editable notes widget and a looping YouTube video player',
		'Draggable, resizable layout with saved themes, background images and per-widget settings'
	];

	const stack = ['Tauri 2', 'Rust', 'React 19', 'TypeScript', 'Tailwind CSS', 'Vite'];
</script>

<svelte:head>
	<title>dashboard-me | David Jennings</title>
	<meta
		name="description"
		content="dashboard-me is a customizable Windows dashboard with a beta macOS build for weather, media, football, notes, links and app shortcuts."
	/>
</svelte:head>

<main class="min-h-screen bg-zinc-950 font-sans text-zinc-100">
	<div class="mx-auto max-w-3xl px-6 py-16 sm:py-24">
		<a
			href="/"
			class="text-sm text-zinc-400 underline decoration-zinc-700 underline-offset-4 transition hover:text-white hover:decoration-zinc-400"
		>
			← David Jennings
		</a>

		<header class="mt-10 flex flex-col gap-5 sm:flex-row sm:items-center">
			<img
				src="/images/dashboard-me-icon.png"
				alt="dashboard-me app icon"
				class="h-20 w-20 rounded-2xl shadow-lg shadow-black/40"
				width="80"
				height="80"
			/>
			<div>
				<p class="text-xs font-medium tracking-wider text-amber-400 uppercase">
					Windows + macOS (Beta) desktop app
				</p>
				<h1 class="mt-1 text-3xl font-semibold tracking-tight text-white sm:text-4xl">
					dashboard-me
				</h1>
				<p class="mt-2 max-w-xl text-zinc-400">
					A customizable dashboard for the things you check every day: weather, media, football,
					time zones, notes, links and app shortcuts.
				</p>
			</div>
		</header>

		<div class="mt-8 grid gap-3 sm:grid-cols-2">
			{#each downloads as download}
				<div class="rounded-xl border border-zinc-800 bg-zinc-900/40 p-4">
					<a
						href={download.url}
						class={download.primary
							? 'inline-flex w-full items-center justify-center rounded-lg bg-amber-400 px-5 py-3 text-sm font-semibold text-zinc-950 transition hover:bg-amber-300'
							: 'inline-flex w-full items-center justify-center rounded-lg border border-zinc-600 bg-zinc-800 px-5 py-3 text-sm font-semibold text-white transition hover:border-zinc-400 hover:bg-zinc-700'}
					>
						{download.label}
					</a>
					<div class="mt-3 flex items-center justify-between gap-2">
						<p class="text-xs text-zinc-500">{download.meta}</p>
						{#if download.beta}
							<span
								class="shrink-0 rounded-full border border-amber-500/40 bg-amber-400/10 px-2 py-0.5 text-[10px] font-semibold tracking-wider text-amber-400 uppercase"
							>
								Beta
							</span>
						{/if}
					</div>
					<p class="mt-1 text-xs break-all text-zinc-600">{download.file}</p>
				</div>
			{/each}
		</div>
		<p class="mt-3 text-sm text-zinc-500">
			v{version} · Both builds are unsigned · 1.2.1 fixes the macOS startup issue.
		</p>

		<figure class="mt-10">
			<img
				src="/images/dashboard-me.jpg"
				alt="dashboard-me showing weather, now playing, football, world clock, notes, quick links and app shortcuts"
				class="w-full rounded-xl border border-zinc-800 shadow-2xl shadow-black/50"
				width="1600"
				height="965"
				loading="lazy"
			/>
			<figcaption class="mt-3 text-xs text-zinc-500">
				Dashboard with the Midnight theme. Widgets can be moved, resized and configured.
			</figcaption>
		</figure>

		<section class="mt-14" aria-labelledby="features-heading">
			<h2 id="features-heading" class="text-sm font-medium tracking-wider text-zinc-500 uppercase">
				What it does
			</h2>
			<ul class="mt-4 grid gap-2 text-sm text-zinc-300 sm:grid-cols-2" role="list">
				{#each features as feature}
					<li class="flex gap-2">
						<span class="mt-1.5 h-1.5 w-1.5 shrink-0 rounded-full bg-amber-400"></span>
						{feature}
					</li>
				{/each}
			</ul>
			<p class="mt-4 text-sm text-zinc-400">
				Now Playing is Windows-only. macOS does not expose global media sessions to desktop apps, so
				the widget shows an unavailable state there. Every other widget works on both platforms.
			</p>
		</section>

		<section class="mt-14" aria-labelledby="install-heading">
			<h2 id="install-heading" class="text-sm font-medium tracking-wider text-zinc-500 uppercase">
				Install
			</h2>

			<h3 class="mt-5 text-sm font-semibold text-white">Windows</h3>
			<ol class="mt-3 list-decimal space-y-2 pl-5 text-sm text-zinc-300">
				<li>Download <code class="text-zinc-100">{windowsInstaller}</code>.</li>
				<li>
					Run the installer. It installs for the current Windows user and does not need
					administrator rights.
				</li>
				<li>
					If Windows SmartScreen appears, choose <strong class="text-white">More info</strong>
					then <strong class="text-white">Run anyway</strong>. The installer is not code-signed.
				</li>
				<li>
					The app opens its first-run setup for name, theme, weather location and football
					preferences.
				</li>
			</ol>
			<p class="mt-4 text-sm text-zinc-400">
				dashboard-me uses Microsoft Edge WebView2. Windows 11 and current Windows 10 include it; the
				installer downloads it if it is missing, so the first install needs an internet connection.
			</p>

			<h3 class="mt-8 text-sm font-semibold text-white">macOS (Beta)</h3>
			<ol class="mt-3 list-decimal space-y-2 pl-5 text-sm text-zinc-300">
				<li>Download <code class="text-zinc-100">{macInstaller}</code> and open it.</li>
				<li>Drag <strong class="text-white">dashboard-me</strong> to Applications.</li>
				<li>
					Launch the app. If Gatekeeper blocks it, right-click the app, choose
					<strong class="text-white">Open</strong>, then confirm
					<strong class="text-white">Open</strong> once.
				</li>
			</ol>
			<p class="mt-4 text-sm text-zinc-400">
				macOS support is in beta. Requires macOS 11 Big Sur or later. The DMG is a universal build
				for Intel and Apple Silicon and is ad-hoc signed, not notarised.
			</p>
		</section>

		<section class="mt-14" aria-labelledby="data-heading">
			<h2 id="data-heading" class="text-sm font-medium tracking-wider text-zinc-500 uppercase">
				Your data
			</h2>
			<p class="mt-4 text-sm text-zinc-400">
				There is no account and no telemetry. Layout, theme, notes and widget settings are stored
				locally under <code class="text-zinc-200">%APPDATA%\com.davi1999.dashboardme</code> on
				Windows and
				<code class="text-zinc-200">~/Library/Application Support/com.davi1999.dashboardme</code>
				on macOS.
			</p>
			<p class="mt-3 text-sm text-zinc-400">
				An optional 5DollarFootballAPI key is kept in Windows Credential Manager or macOS Keychain,
				not in the dashboard file. Weather, football, quotes and YouTube playback require an
				internet connection.
			</p>
			<p class="mt-3 text-sm text-zinc-400">
				The app is built from a private source repository; this page distributes the compiled
				installers only.
			</p>
		</section>

		<section class="mt-14" aria-labelledby="stack-heading">
			<h2 id="stack-heading" class="text-sm font-medium tracking-wider text-zinc-500 uppercase">
				Built with
			</h2>
			<ul class="mt-4 flex flex-wrap gap-2" role="list">
				{#each stack as item}
					<li>
						<span
							class="inline-block rounded-md border border-zinc-700 bg-zinc-900 px-3 py-1 text-sm text-zinc-300"
						>
							{item}
						</span>
					</li>
				{/each}
			</ul>
		</section>

		<section class="mt-14 rounded-lg border border-zinc-800 bg-zinc-900/50 p-5">
			<h2 class="text-sm font-semibold text-white">Verify the downloads</h2>
			<p class="mt-2 text-sm text-zinc-400">
				Compare each file's SHA-256 hash with the values below:
			</p>
			<div class="mt-3 space-y-4">
				{#each downloads as download}
					<div>
						<p class="text-xs font-medium text-zinc-400">{download.platform}</p>
						<code
							class="mt-1 block overflow-x-auto rounded-md bg-zinc-950 p-3 text-xs text-zinc-300"
						>
							{download.hash}
						</code>
					</div>
				{/each}
			</div>
			<p class="mt-4 text-sm text-zinc-400">
				<a
					href={releaseUrl}
					class="text-amber-400 underline decoration-amber-600 underline-offset-2 hover:decoration-amber-400"
					target="_blank"
					rel="noopener noreferrer"
				>
					Release notes and checksums
				</a>
			</p>
		</section>

		<footer class="mt-16 border-t border-zinc-800 pt-6">
			<a
				href="/"
				class="text-sm text-zinc-400 underline decoration-zinc-700 underline-offset-4 transition hover:text-white hover:decoration-zinc-400"
			>
				← Back to home
			</a>
		</footer>
	</div>
</main>
