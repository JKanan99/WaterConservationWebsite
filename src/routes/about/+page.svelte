<script>
  import dania from "$lib/images/dania.jpeg"
  import jahnvi from "$lib/images/jahnvi.jpeg"
  import jennah from "$lib/images/jennah.jpeg"
  const members = [
    {
      img: jahnvi,
      name: "Jahnvi Panchal",
      description:
        "I am a computer science major who enjoys front end development. My hobbies are reading, hiking, dancing, and playing with my puppy!",
      email: "jahnvi@csu.fullerton.edu",
    },
    {
      img: jennah,
      name: "Jennah Kanan",
      description: "I'm a senior at CSUF majoring in computer science. My hobbies inlude baking, hiking, and sitting at coffee shops with friends!",
      email: "jkanan@csu.fullerton.edu",
    },
    {
      img: dania,
      name: "Dania Nasereddin",
      description:
        "Hello! I'm Dania! I am a computer science major at CSUF. I love playing video games, walking my dog, and painting in my free time!",
      email: "dnasereddin@csu.fullerton.edu",
    },
  ];
</script>

<svelte:head>
  <title>ABOUT | Water Conservation</title>
  <meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
  {#each members as { img, name, description, email }}
    <div class="card">
      <div class="content">
        <img src={img} alt={name} />
        <h2>{name}</h2>
        <p>Team Member</p>
        <p>{description}</p>
        <p>{email}</p>
      </div>
      <a class="button" href={`mailto:${email}`} target="_blank">Contact</a>
    </div>
  {/each}
</section>

<style>
  section {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 32px;
  }

  section .card {
    display: flex;
    flex-direction: column;
    max-width: 320px;
    width: 100%;
    justify-content: space-between;
    gap: 16px;
    padding: 32px;
    border-radius: 8px;
    background-color: white;
    filter: drop-shadow(0px 4px 16px rgba(0, 0, 0, 0.1));
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .content img {
    width: 100%;
    max-height: 256px;
    height: 100%;
    border: 1px solid black;
    border-radius: 4px;
    object-fit: cover;
    object-position: 10% 0;
  }

  .button {
    padding: 8px;
    background-color: #00ace5;
    color: white;
    border-radius: 4px;
    text-align: center;
    text-decoration: none;
    transition: background-color 100ms ease-in-out;
  }

  .button:hover {
    background-color: #006d8f;
  }
</style>
