
<template>
  <article :class="['card', { featured: tier.featured }]">
    <img v-if="tier.image" :src="tier.image" :alt="tier.name + ' image'" />

    <button
      class="fav-btn"
      :class="{ fav: tier.favourited }"
      @click="$emit('toggle-fav', tier)"
      :aria-pressed="tier.favourited ? 'true' : 'false'"
      :aria-label="tier.favourited ? 'Unfavourite ' + tier.name : 'Favourite ' + tier.name"
      title="Toggle favourite"
    >
      ♥
    </button>

    <div class="card-body">
      <h2>{{ tier.name }}</h2>
      <div class="price">R {{ tier.price }}</div>

      <ul class="benefits">
        <li v-for="(b, i) in tier.benefits" :key="i">✔ {{ b }}</li>
      </ul>
    </div>
  </article>
</template>

<script setup>
defineProps({ tier: Object })
defineEmits(['toggle-fav'])
</script>

<style scoped>
.card {
  background: rgba(255, 255, 255, 0.04);
  padding: 18px;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.08);
}
.card.featured {
  border-color: #7c3aed;
  background: rgba(124, 58, 237, 0.1);
}
.price {
  font-size: 20px;
  font-weight: 800;
}
.fav.active { color: #7c3aed }
.benefits { margin: 12px 0; padding-left: 18px }
.fav-btn { position: absolute; top: 12px; right: 12px; border: none; background: transparent; color: #ddd; font-size: 1.4rem; cursor: pointer; transition: transform .12s ease, color .18s ease; padding:6px; border-radius:8px }
.fav-btn.fav { color: #ff4da6; transform: scale(1.14); text-shadow: 0 0 6px rgba(255,77,150,0.6) }
.fav-btn:focus { outline: 3px solid rgba(255,77,150,0.12); }
.fav-btn:focus-visible { outline: 3px solid rgba(255,77,150,0.22); }
.card { position: relative; overflow: hidden }
</style>
