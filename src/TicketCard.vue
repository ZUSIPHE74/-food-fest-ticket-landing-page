<template>
  <div class="card" :class="{ featured: tier.featured }">
    <img :src="tier.image" alt="ticket image" />

    <div
      class="fav-btn"
      :class="{ fav: tier.favourited }"
      @click="$emit('toggle-fav', tier)"
    >
      ♥
    </div>

    <h2>{{ tier.name }}</h2>
    <div class="price">R {{ tier.price }}</div>

    <ul>
      <li v-for="b in tier.benefits" :key="b">{{ b }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    tier: Object
  }
}
</script>

<style scoped>
.card {
  background: #1a1a33;
  border-radius: 18px;
  padding: 20px;
  transition: 0.3s;
  box-shadow: 0 0 10px rgba(255,255,255,0.05);
  position: relative;
}

.card.featured {
  border: 2px solid #aa66ff;
  box-shadow: 0 0 20px rgba(170,102,255,0.5);
}

.card:hover {
  transform: translateY(-5px);
}

img {
  width: 100%;
  height: 150px;
  border-radius: 14px;
  object-fit: cover;
  margin-bottom: 15px;
}

h2 {
  margin: 8px 0 5px;
}

.price {
  font-size: 1.4rem;
  font-weight: bold;
  color: #aa88ff;
}

ul {
  padding-left: 20px;
}

.fav-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 22px;
  cursor: pointer;
  transition: 0.25s;
}

.fav-btn.fav {
  color: #ff4da6;
  text-shadow: 0 0 10px #ff4da6;
}
</style>
