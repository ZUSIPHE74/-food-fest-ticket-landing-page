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

            <button class="fav-btn" @click.stop="addFavourite(ticket)">
               Favourite
            </button>

            <button class="notify-btn" @click.stop="notifyUser(ticket.title)">
              Notify Me
            </button>
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

    <!-- FAVOURITES LIST -->
    <section class="favourites" v-if="favourites.length > 0">
      <h2>Your Favourite Tickets</h2>
      <ul>
        <li v-for="(fav, index) in favourites" :key="index">
          {{ fav.title }} – {{ fav.price }}
        </li>
      </ul>
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
          image: "./images/bronze.jpg",
          benefits: ["General Entry", "Live Music"],
          flip: false
        },
        {
          title: "Silver Ticket",
          price: "R300",
          image: "./images/silver.jpg",
          benefits: ["General Entry", "Live Music", "Free Drink"],
          flip: false
        },
        {
          title: "Gold Ticket",
          price: "R600",
          image: "./images/Gold.jpg",
          benefits: ["VIP Lounge", "Backstage Access", "Unlimited Meals"],
          flip: false
        }
      ],

      //  Store favourites here
      favourites: []
    };
  },

  methods: {
    addFavourite(ticket) {
      // Avoiding duplicating favourites
      const exists = this.favourites.find(f => f.title === ticket.title);
      if (!exists) {
        this.favourites.push(ticket);
        alert(`${ticket.title} added to favourites `);
      } else {
        alert(`${ticket.title} is already in your favourites.`);
      }
    },

    notifyUser(ticketName) {
      alert(`You will be notified when sales start for ${ticketName}!`);
    }
  }
};
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

/* Buttons */
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

.fav-btn {
  background: #ff4d9e;
}

.notify-btn {
  background: #0055ff;
}

/* Favourites */
.favourites {
  margin-top: 40px;
}

.favourites h2 {
  color: #ffccff;
  margin-bottom: 10px;
}

.favourites ul {
  list-style: none;
  padding: 0;
}

.favourites li {
  background: #260066;
  padding: 10px;
  margin: 8px auto;
  width: 300px;
  border-radius: 12px;
}
</style>
