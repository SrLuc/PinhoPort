<script setup>
const props = defineProps({
  title: { type: String, required: true },
  idealFor: { type: String, required: true },
  prices: { type: Array, required: true }, // [{ label: 'Mensal', value: 'R$ 89,90' }, ...]
  imgSrc: { type: String, required: true },
  ctaText: { type: String, required: true },
  ctaLink: { type: String, required: true },
});
</script>

<template>
  <a :href="ctaLink" class="plan-card" target="_blank" rel="noopener">
    <img :src="imgSrc" alt="Imagem do plano" class="plan-img" />

    <div class="plan-content">
      <h3>{{ title }}</h3>
      <p class="plan-ideal"><strong>Ideal para:</strong> {{ idealFor }}</p>

      <div class="plan-prices">
        <div v-for="(price, index) in prices" :key="index" class="plan-price">
          <span class="price-label">{{ price.label }} — </span>
          <span class="price-value">{{ price.value }}</span>
        </div>
      </div>

      <span class="plan-cta">{{ ctaText }}</span>
    </div>
  </a>
</template>

<style scoped>
.plan-card {
  display: flex;
  align-items: center;
  background: #f5f5f5;
  border-radius: 12px;
  padding: 1rem;
  margin-bottom: 1rem;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  text-decoration: none;
  transition: background 0.3s, color 0.3s;
  flex-wrap: wrap;
}
.plan-card:hover {
  background: #e0e0e0;
}
.plan-img {
  width: 180px;
  height: 150px;
  object-fit: cover;
  border-radius: 10px;
  margin-right: 1rem;
}
.plan-content {
  flex: 1;
}
.plan-content h3 {
  font-size: 1.2rem;
  color: #222;
  margin-bottom: 0.3rem;
}
.plan-ideal {
  color: #555;
  margin-bottom: 0.8rem;
}
.plan-prices {
  margin-bottom: 1rem;
}
.plan-price {
  margin-bottom: 0.4rem;
  font-size: 0.95rem;
  color: #333;
}
.price-label {
  font-weight: bold;
}
.price-value {
  color: #111;
}
.plan-cta {
  display: inline-block;
  background-color: #4caf50;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-weight: bold;
  transition: background 0.3s;
  font-size: 0.95rem;
  cursor: pointer;
}
.plan-cta:hover {
  background-color: #45a049;
}

/* Dark mode */
body.dark .plan-card {
  background: #383b3f;
  color: #e8eaed;
}
body.dark .plan-card:hover {
  background: #5f6368;
}
body.dark .plan-ideal,
body.dark .plan-price {
  color: #ccc;
}

@media (max-width: 600px) {
  .plan-card {
    flex-direction: column;
    align-items: flex-start;
  }
  .plan-img {
    margin-right: 0;
    margin-bottom: 1rem;
    width: 100%;
    height: 50%;
  }

  .plan-cta {
    text-align: center;
    width: 100%;
    padding: 0.7rem 0;
    margin-top: 0.5rem;
  }

  
}

</style>
