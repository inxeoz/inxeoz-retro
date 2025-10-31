<script>
  export let title;
  export let description;
  export let image = '/placeholder.jpg';
  export let link = '#';
</script>

<article class="card-bw">
  <div class="border-b-2 mb-3">
    <img class="project-thumbnail w-full h-40 object-cover" src={image} alt={title} />
  </div>
  <h3 class="font-bold text-lg">{title}</h3>
  <p class="mt-2 text-sm">{description}</p>
  <div class="mt-4">
    <a class="inline-block px-3 py-2 border-2" href={link}>View project</a>
  </div>
</article>