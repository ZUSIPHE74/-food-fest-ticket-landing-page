<template>
  <div class="container">

    <!-- INTRO -->
    <section class="intro">
      <h1>Cape Town Food Fest 2025</h1>
      <p>
        A weekend filled with flavours, music, culture and unforgettable experiences!
        Explore our exciting ticket options below.
      </p>

      <img src="https://media.timeout.com/images/101887547/image.jpg" class="hero" />
    </section>

    <!-- TICKETS -->
    <section class="tickets">
      <h2>Choose Your Ticket</h2>

      <div class="grid">
        <div 
          class="card" 
          v-for="ticket in tickets" 
          :key="ticket.title"
          @click="ticket.flip = !ticket.flip"
        >
          <!-- FRONT -->
          <div v-if="!ticket.flip" class="front">
            <img :src="ticket.image" />
            <h3>{{ ticket.title }}</h3>
            <p class="price">{{ ticket.price }}</p>
          </div>

          <!-- BACK -->
          <div v-else class="back">
            <h3>{{ ticket.title }} Benefits</h3>

            <ul>
              <li v-for="(b, i) in ticket.benefits" :key="i">{{ b }}</li>
            </ul>

            <button>Buy Now</button>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script>
export default {
  data() {
    return {
      tickets: [
        {
          title: "Bronze Ticket",
          price: "R150",
          image: "https://lh3.googleusercontent.com/gg-dl/ABS2GSkBfdRZq-cE1_lH4rSVwA-T73QlJJSfOWhu2MaP1ZFglyux4HX3xnjuxuYTpR1NEmNNW4sDK4RLsnvlESckYI7yin8BKihpPATsZcfd90bjWc0STCVkRE-MAEOYR27MVAcgHzgzNa6rZ4kRD3APzn68Dsd3OlF2kYJXEBbaGN4dZnVj=s1024-rj",
          benefits: [
            "General Entry",
            "Live Music"
          ],
          flip: false
        },
        {
          title: "Silver Ticket",
          price: "R300",
          image: "https://lh3.googleusercontent.com/gg-dl/ABS2GSkzcFn_f7CkNL9_nB7o4IpYlKuhaBjeihdOGV5xDQW2cWEq9gsdthSBcqiJDRdDtck4AbSi_xecCpZ-DyWy-iQhj9ac8A1mYZm59wiwEMIN95vPvf6G7ywIBddD-A_ForbJZurgFj3vZE54n-VmjVKrwzWTBxs79-II_8dk1AXW2HLKoA=s1024-rj",
          benefits: [
            "General Entry",
            "Live Music",
            "Free Drink"
          ],
          flip: false
        },
        {
          title: "Gold Ticket",
          price: "R600",
          image: "https://lh3.googleusercontent.com/gg-dl/ABS2GSkUKWeJlPfpCAEyAESxDQfDXAOPB3G4SdshXS_lFVdMMfo3z692N7q9mkR9jKOi6vKP3_uC7nS2cxAyB9j0OgpMamNXB8aHzmykFRAoVen0WHrLcCPu-B-TnHQcPlzmCgoMuVTNmfXMpxYIzxtoa65wtoR4nkQoDej5S96snQVTrPY=s1024-rj",
          benefits: [
            "VIP Lounge",
            "Backstage Access",
            "Unlimited Meals"
          ],
          flip: false
        }
      ]
    }
  }
}
</script>

<style>
body {
  margin: 0;
  background: #0a0020;
  font-family: "Poppins", sans-serif;
  color: white;
}

/* Container */
.container {
  padding: 20px;
  text-align: center;
}

/* Intro */
.intro h1 {
  font-size: 2.2rem;
  color: #ff33d4;
  margin-bottom: 10px;
}

.intro p {
  max-width: 500px;
  margin: auto;
  opacity: 0.8;
}

.hero {
  width: 80%;
  margin-top: 20px;
  border-radius: 20px;
}

/* Tickets */
.tickets h2 {
  margin-top: 40px;
  color: #e8b3ff;
}

.grid {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 25px;
}

/* Cards */
.card {
  background: #1a0046;
  width: 260px;
  padding: 20px;
  border-radius: 18px;
  cursor: pointer;
  transition: 0.3s;
}

.card:hover {
  transform: scale(1.05);
}

.front img {
  width: 100%;
  border-radius: 12px;
}

.price {
  margin-top: 10px;
  font-size: 1.1rem;
  color: #ff9aff;
}

.back ul {
  text-align: left;
  padding-left: 20px;
}

button {
  margin-top: 10px;
  padding: 10px;
  width: 100%;
  background: #ff00c8;
  border: none;
  color: white;
  font-weight: bold;
  border-radius: 10px;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
</style>
