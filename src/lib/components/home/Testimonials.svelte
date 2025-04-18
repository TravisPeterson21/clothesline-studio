
<script>
  import { Linkedin, Github } from 'lucide-svelte';

  const testimonials = [
    {
      quote: "Travis is a powerhouse — thoughtful, creative, and reliable. He brings order to chaos and always finds a smart path forward.",
      name: "Emily Rang",
      title: "Senior Consultant, AEM Corporation",
      img: "/image/emilyrang.jpg",
      linkedin: "https://www.linkedin.com/in/emilycrang/"
    },
    {
      quote: "Working with Travis was a game-changer. He blends technical skill with serious design sense.",
      name: "Jim Campbell",
      title: "Director, CIID",
      img: "/image/jimcampbell.jpg",
      linkedin: "https://www.linkedin.com/in/jimcampbellprofile/"
    },
    {
      quote: "From strategy to execution, Travis delivers. Every. Single. Time.",
      name: "Andrew Hinkle",
      title: "OSEP Program Officer",
      img: "/image/andrewhinkle.jpg"
    }
  ];
</script>

<section class="bg-[var(--color-bg)] text-[var(--color-text)] py-20 px-6 sm:px-12 md:px-20 lg:px-32 transition-colors duration-300">
  <div class="max-w-6xl mx-auto text-center space-y-12">
    <h2 class="text-3xl sm:text-4xl font-bold text-[var(--color-accent)]">What People Say</h2>

    <div class="grid gap-10 md:grid-cols-2 lg:grid-cols-3">
      {#each testimonials as t}
        <div class="bg-[var(--color-bg)] border border-[var(--color-plum)] rounded-2xl shadow-md p-6 flex flex-col items-center text-center hover:shadow-xl transition">
          
          <!-- 🖼 Image -->
          <img src={t.img} alt={t.name} class="w-20 h-20 rounded-full object-cover border-2 border-[var(--color-accent)] mb-4" />

          <!-- 💬 Quote -->
          <p class="text-sm italic text-[var(--color-text)] mb-4">“{t.quote}”</p>

          <!-- 👤 Name + Title -->
          <div class="text-sm font-semibold text-[var(--color-accent)]">{t.name}</div>
          <div class="text-xs text-[var(--color-slateblue)] mb-3">{t.title}</div>

          <!-- 🔗 Socials -->
          <div class="flex gap-3 justify-center mt-auto">
            {#if t.linkedin}
              <a href={t.linkedin} target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
                <Linkedin size="18" />
              </a>
            {/if}
            {#if t.github}
              <a href={t.github} target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
                <Github size="18" />
              </a>
            {/if}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

  