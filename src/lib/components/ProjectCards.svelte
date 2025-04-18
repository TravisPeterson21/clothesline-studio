<script lang="ts">
    import { gsap } from 'gsap';
    import gestures from 'svelte-gestures';
    const { swipe } = gestures;
  
    let activeProjectIndex = 0;
    let activeSectionIndex = 0;
    let cardEl: HTMLDivElement | null = null;
  
    const sectionKeys = ['summary', 'role', 'tools', 'challenges', 'outcomes'];
  
    const projects = [
      {
        title: 'G3 Drupal Website',
        summary: 'Led the development of a standalone site for the Generate Governance Group.',
        role: [
          'Primary point of contact for Drupal site build',
          'Designed G3 logo and deck template',
          'Migrated content from Communities360'
        ],
        tools: ['Drupal', 'Illustrator', 'PowerPoint', 'GitHub', 'Communities360'],
        challenges: [
          { title: 'Inflexible legacy platform', solution: 'Moved to Drupal with a custom structure' },
          { title: 'No visual identity', solution: 'Created modern logo and branding' }
        ],
        outcomes: [
          'Standalone branded site',
          'Improved access to governance content',
          'Boosted stakeholder engagement'
        ]
      },
      // Add more projects here...
    ];
  
    function nextSection() {
      gsap.to(cardEl, {
        x: -100,
        opacity: 0,
        duration: 0.3,
        onComplete: () => {
          activeSectionIndex = (activeSectionIndex + 1) % sectionKeys.length;
          gsap.fromTo(cardEl, { x: 100, opacity: 0 }, { x: 0, opacity: 1, duration: 0.3 });
        }
      });
    }
  
    function prevSection() {
      gsap.to(cardEl, {
        x: 100,
        opacity: 0,
        duration: 0.3,
        onComplete: () => {
          activeSectionIndex = (activeSectionIndex - 1 + sectionKeys.length) % sectionKeys.length;
          gsap.fromTo(cardEl, { x: -100, opacity: 0 }, { x: 0, opacity: 1, duration: 0.3 });
        }
      });
    }
  
    function switchProject(index: number) {
      activeProjectIndex = index;
      activeSectionIndex = 0;
    }
  </script>
  
  <section class="max-w-4xl mx-auto px-6 py-12">
    <!-- Project Tabs -->
    <div class="flex flex-wrap gap-3 mb-6">
      {#each projects as project, i}
        <button
          on:click={() => switchProject(i)}
          class="px-4 py-2 text-sm font-semibold rounded-md border transition"
          class:bg-orange-500={activeProjectIndex === i}
          class:bg-slate-800={activeProjectIndex !== i}
          class:text-white
        >
          {project.title}
        </button>
      {/each}
    </div>
  
    <!-- Card -->
    <div
      bind:this={cardEl}
      use:swipe
      on:swipe={({ detail }: { detail: { direction: 'LEFT' | 'RIGHT' } }) => {
        if (detail.direction === 'LEFT') nextSection();
        if (detail.direction === 'RIGHT') prevSection();
      }}
      class="bg-[#171123] rounded-2xl shadow-xl p-8 text-white transition-all duration-300 space-y-4"
    >
      <h2 class="text-2xl font-bold text-orange-400">
        {projects[activeProjectIndex].title}
      </h2>
  
      {#if sectionKeys[activeSectionIndex] === 'summary'}
        <p class="text-lg italic text-slate-300">
          {projects[activeProjectIndex].summary}
        </p>
  
      {:else if sectionKeys[activeSectionIndex] === 'role'}
        <div>
          <h3 class="font-semibold text-lg mb-2">🧠 My Role</h3>
          <ul class="list-disc list-inside text-slate-200">
            {#each projects[activeProjectIndex].role as item}
              <li>{item}</li>
            {/each}
          </ul>
        </div>
  
      {:else if sectionKeys[activeSectionIndex] === 'tools'}
        <div>
          <h3 class="font-semibold text-lg mb-2">🛠️ Tools & Tech</h3>
          <div class="flex flex-wrap gap-2">
            {#each projects[activeProjectIndex].tools as tool}
              <span class="bg-slate-800 px-3 py-1 rounded-full text-sm">
                {tool}
              </span>
            {/each}
          </div>
        </div>
  
      {:else if sectionKeys[activeSectionIndex] === 'challenges'}
        <div>
          <h3 class="font-semibold text-lg mb-2">🚧 Challenges & Solutions</h3>
          <ul class="text-slate-200 space-y-2">
            {#each projects[activeProjectIndex].challenges as ch}
              <li>
                <strong>{ch.title}</strong><br />
                <em class="ml-2">Solution:</em> {ch.solution}
              </li>
            {/each}
          </ul>
        </div>
  
      {:else if sectionKeys[activeSectionIndex] === 'outcomes'}
        <div>
          <h3 class="font-semibold text-lg mb-2">🌟 Outcomes & Impact</h3>
          <ul class="list-disc list-inside text-slate-200">
            {#each projects[activeProjectIndex].outcomes as o}
              <li>{o}</li>
            {/each}
          </ul>
        </div>
      {/if}
    </div>
  
    <!-- Nav Buttons -->
    <div class="flex justify-between mt-6">
      <button on:click={prevSection} class="bg-slate-700 hover:bg-slate-600 text-white px-4 py-2 rounded-lg">
        ← Back
      </button>
      <button on:click={nextSection} class="bg-slate-700 hover:bg-slate-600 text-white px-4 py-2 rounded-lg">
        Next →
      </button>
    </div>
  </section>
  
  
  