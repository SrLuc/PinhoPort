<script setup>
const props = defineProps({
  title: { type: String, required: true },
  text: { type: String, required: true },
  imgSrc: { type: String, required: true },
  link: { type: String, required: true },
});
</script>

<template>
  <a :href="link" class="card" target="_blank" rel="noopener">
    <img :src="imgSrc" alt="Card Image" class="card-img" />
    <div class="card-content">
      <h3>{{ title }}</h3>
      <p>{{ text }}</p>
    </div>
  </a>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
  text-decoration: none;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.card {
  display: flex;
  align-items: center;
  background: #f5f5f5;
  border-radius: 12px;
  padding: 1rem;
  margin-bottom: 1rem;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  transition: background 0.3s, color 0.3s;
  flex-wrap: wrap;
}
.card:hover {
  background: #e0e0e0;
}
.card-img {
  width: 180px;
  height: 150px;
  object-fit: cover;
  border-radius: 10px;
  margin-right: 1rem;
}
.card-content h3 {
  font-size: 1.1rem;
  color: #222;
  margin-bottom: 0.3rem;
}
.card-content p {
  color: #555;
}
body.dark .card {
  background: #383 b3f;
  color: #e8eaed;
}
body.dark .card:hover {
  background: #5f6368;
}
body.dark .card-content p {
  color: #ccc;
}

@media (max-width: 600px) {
  .card {
    flex-direction: column;
    align-items: flex-start;
  }
  .card-img {
    margin-right: 0;
    margin-bottom: 1rem;
    width: 100%;
    height: auto;
  }
}

</style>
