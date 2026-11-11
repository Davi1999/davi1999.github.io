<script lang="ts">
	const links = [
		{ label: 'GitHub', href: 'https://github.com/Davi1999' },
		{ label: 'LinkedIn', href: 'https://www.linkedin.com/in/david-jennings-1a3997191/' }
	];

	const tech = ['React', 'PHP', 'Next.js', 'Python', 'AWS'];

	const projects = [
		{
			name: 'dashboard-me',
			href: '/projects/dashboard-me',
			description:
				'A customizable Windows and macOS dashboard for weather, media, football, notes, links and app shortcuts.',
			external: false
		},
		{
			name: 'The Pigeon Post',
			href: 'https://the-pigeon-post.com/dashboard',
			description:
				'A modern message service with the charm of old-fashioned letters—for small communities and creative teams.',
			external: true
		}
	];
</script>

<svelte:head>
	<title>David Jennings | Software Engineer</title>
</svelte:head>

<main class="min-h-screen bg-zinc-950 font-sans text-zinc-100">
	<div class="mx-auto max-w-2xl px-6 py-16 sm:py-24">
		<header class="mb-16">
			<h1 class="text-3xl font-semibold tracking-tight text-white sm:text-4xl">David Jennings</h1>
			<p class="mt-2 text-lg text-zinc-400">Software Engineer</p>
			<nav class="mt-6 flex gap-6" aria-label="External links">
				{#each links as link}
					<a
						href={link.href}
						target="_blank"
						rel="noopener noreferrer"
						class="text-zinc-400 underline decoration-zinc-600 underline-offset-4 transition hover:text-white hover:decoration-zinc-400"
					>
						{link.label}
					</a>
				{/each}
			</nav>
		</header>

		<section class="mb-14" aria-labelledby="experience-heading">
			<h2
				id="experience-heading"
				class="text-sm font-medium tracking-wider text-zinc-500 uppercase"
			>
				Experience
			</h2>
			<div class="mt-4">
				<p class="text-zinc-300">
					<strong class="text-white">Fullstack Developer</strong> at
					<a
						href="https://www.pathful.com/"
						target="_blank"
						rel="noopener noreferrer"
						class="text-amber-400 underline decoration-amber-600 underline-offset-2 hover:decoration-amber-400"
					>
						Pathful
					</a>
					— 3 years building career readiness and development tools for the industry leading K-16 education
					platform.
				</p>
			</div>
		</section>

		<section class="mb-14" aria-labelledby="tech-heading">
			<h2 id="tech-heading" class="text-sm font-medium tracking-wider text-zinc-500 uppercase">
				Tech I work with daily
			</h2>
			<ul class="mt-4 flex flex-wrap gap-2" role="list">
				{#each tech as t}
					<li>
						<span
							class="inline-block rounded-md border border-zinc-700 bg-zinc-900 px-3 py-1 text-sm text-zinc-300"
						>
							{t}
						</span>
					</li>
				{/each}
			</ul>
		</section>

		<section aria-labelledby="projects-heading">
			<h2 id="projects-heading" class="text-sm font-medium tracking-wider text-zinc-500 uppercase">
				Personal projects
			</h2>
			<ul class="mt-4 space-y-4" role="list">
				{#each projects as project}
					<li class="rounded-lg border border-zinc-800 bg-zinc-900/50 p-4">
						<a
							href={project.href}
							target={project.external ? '_blank' : undefined}
							rel={project.external ? 'noopener noreferrer' : undefined}
							class="font-medium text-white underline decoration-zinc-600 underline-offset-2 hover:decoration-amber-500"
						>
							{project.name}
						</a>
						<p class="mt-1 text-sm text-zinc-400">
							{project.description}
						</p>
					</li>
				{/each}
			</ul>
		</section>
	</div>
</main>
