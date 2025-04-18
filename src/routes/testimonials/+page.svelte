<script>
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  import { Linkedin, Github } from 'lucide-svelte';

  gsap.registerPlugin(ScrollTrigger);

  const testimonials = [
    {
      text: "Travis is the rare mix of thoughtful, technically sharp, and wildly creative.",
      author: "Jim Campbell, VP, AEM Corporation",
      img: "/image/jimcampbell.jpg",
      linkedin: "https://www.linkedin.com/in/jimcampbellprofile/",
      logo: "/image/aemlogo.webp" // ✅ Add this
    },
    {
      text: "One of the most dependable and versatile creatives I've ever worked with.",
      author: "Bill Huennekens, Director, AEM Corporation",
      img: "/image/billhuennekens.jpg",
      linkedin: "https://www.linkedin.com/in/bill-huennekens-9536483/"
    },
    {
      text: "Brilliant at taking complex systems and turning them into intuitive experiences.",
      author: "Emily Range, CIID Deputy Director, AEM Corporation",
      img: "/image/emilyrang.jpg",
      linkedin: "https://www.linkedin.com/in/emilycrang/"
    },
    {
      text: "Brilliant at taking complex systems and turning them into intuitive experiences.",
      author: "Nancy Copa, Senior Assistant Director, AEM Corporation",
      img: "/image/nancycopa.jpg",
      linkedin: "https://www.linkedin.com/in/nancy-copa-83110a85/"
    },
    {
      text: "Brilliant at taking complex systems and turning them into intuitive experiences.",
      author: "Johnny Cunningham, Generate Developer, AEM Corporation",
      img: "/image/johnnycunningham.jpg",
      linkedin: "https://www.linkedin.com/in/johnny-cunningham-2704145/",
      github: "https://github.com/AEMJohnnyCunningham"
    },
    {
      text: "Brilliant at taking complex systems and turning them into intuitive experiences.",
      author: "Nathan Clinton, Generate Developer, AEM Corporation",
      img: "/image/nathanclinton.jpg",
      linkedin: "https://www.linkedin.com/in/emilycrang/",
      github: "https://github.com/AEMJohnnyCunningham"
    }
  ];

  onMount(() => {
    gsap.utils.toArray('.testimonial').forEach((el) => {
      gsap.from(el, {
        scrollTrigger: {
          trigger: el,
          start: 'top 85%',
          toggleActions: 'play none none none'
        },
        opacity: 0,
        y: 30,
        duration: 0.6,
        ease: 'power2.out'
      });
    });
  });
</script>

<section class="mx-auto py-16 px-4 text-[var(--color-text)]">
  <h1 class="text-4xl font-bold text-[var(--color-accent)] mb-4">Testimonials</h1>
  <p class="text-lg text-[var(--color-slateblue)] mb-10">
    Words from collaborators, clients, and colleagues.
  </p>

  <div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
    {#each testimonials as t}
      <div class="testimonial p-6 bg-[var(--color-bg)] border border-[var(--color-plum)] rounded-xl shadow-md transition hover:shadow-xl group">
        <!-- Profile + Logo Row -->
        <div class="flex justify-between items-center mb-4">
          <div class="flex items-center gap-4">
            <img src={t.img} alt={t.author} class="w-12 h-12 rounded-full object-cover border border-[var(--color-slateblue)]" />
            <div>
              <p class="font-semibold text-[var(--color-accent)]">{t.author}</p>
              <div class="flex gap-2 mt-1">
                {#if t.linkedin}
                  <a href={t.linkedin} target="_blank" rel="noopener noreferrer" class="text-[var(--color-indigo)] hover:text-[var(--color-accent)] transition">
                    <Linkedin size="16" />
                  </a>
                {/if}
                {#if t.github}
                  <a href={t.github} target="_blank" rel="noopener noreferrer" class="text-[var(--color-indigo)] hover:text-[var(--color-accent)] transition">
                    <Github size="16" />
                  </a>
                {/if}
              </div>
            </div>
          </div>
          {#if t.logo}
  <div class="bg-white p-2 rounded-full shadow-sm flex items-center justify-center h-10 w-10">
    <img src={t.logo} alt="Company logo" class="h-6 w-6 object-contain" />
  </div>
{/if}
        </div>

        <!-- Quote -->
        <p class="italic text-[var(--color-text)]">"{t.text}"</p>
      </div>
    {/each}
  </div>
</section> <!-- ✅ Close the section only once, outside the loop -->




  