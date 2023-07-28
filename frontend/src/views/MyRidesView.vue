<script>
import axios from 'axios';
import main_title from '../components/main_title.vue';
import Rate from '../components/rate.vue';
import navbar from '../components/navbar.vue';
import banner from '../components/banner.vue';
import { getBookedRides } from "../composables/ridesApi.js";

export default {
  components: {
    main_title,
    navbar,
    banner,
    Rate
  },
  data() {
    return {
      bookedRides: null,
      error: null,
      departureAddresses: {},
      destinationAddresses: {}
    };
  },
  async created() {
    try {
      const { bookedRides, error } = await getBookedRides();
      this.bookedRides = bookedRides;
      this.error = error;

      this.fetchAddresses();
    } catch (error) {
      this.error = 'Failed to fetch booked rides';
    }
  },

  methods: {
    onClick(id) {
      if (id) {
        this.$router.push({ name: 'BookedRide', params: { id: id } });
      } else {
        console.error('Invalid ride id');
      }
    },

    async getAddressFromCoordinates(latitude, longitude) {
      try {
        const response = await axios.get('https://maps.googleapis.com/maps/api/geocode/json', {
          params: {
            latlng: `${latitude},${longitude}`,
            key: 'API_KEY',
          },
        });

        if (response.data.results.length > 0) {
          const address = response.data.results[0].formatted_address;
          return address;
        } else {
          throw new Error('No results found');
        }
      } catch (error) {
        return 'Unknown address';
      }
    },

    async fetchAddresses() {
      for (const ride of this.bookedRides) {
        const departureAddress = await this.getAddressFromCoordinates(
          ride.departure.lat,
          ride.departure.long
        );
        this.departureAddresses[ride._id] = departureAddress;

        const destinationAddress = await this.getAddressFromCoordinates(
          ride.destination.lat,
          ride.destination.long
        );
        this.destinationAddresses[ride._id] = destinationAddress;
      }
    },

    getCardClass(index) {
      return index % 2 === 0 ? 'card pink white' : 'card bg-teal white';
    },
    getLimitedAddress(address) {
      const words = address.split(' ');
      if (words.length > 5) {
        return words.slice(0, 5).join(' ') + '...';
      } else {
        return address;
      }
    },
  },
};
</script>

<template>
  <div>
    <main_title title="Airport Bound! 🚀 Buckle Up and Let's Go!" />
    <h3 class="card-title"> 🛫 Upcoming Airport Adventures</h3>
    <div class="card-container">
      <div @click="onClick(ride._id)" :class="getCardClass(index)" v-for="(ride, index) in bookedRides" :key="ride._id">
        <div class="wrapper center">
          <p class="title">{{ getLimitedAddress(destinationAddresses[ride._id]) }}</p>
        </div>
        <div class="wrapper">
          <div class="time-column">
            <p class="card-time">{{ ride.departure_time }}</p>
          </div>
          <div class="time-column">
            <p class="card-time">{{ ride.destination_time }}</p>
          </div>
        </div>
        <div class="wrapper">
          <div class="left-section">
            <img src="../../img/driver.svg" alt="Avatar">
            <p class="card-text "> &nbsp;&nbsp;{{ ride.driver }}</p>
          </div>
          <div class="right-section">
            <p>&nbsp;08.06.2023</p>
          </div>
        </div>
      </div>
    </div>

    <h3 class="card-title">🏁 Successful Airport Ventures</h3>
    <div class="card-container">
      <div class="card bg-blue grey">
        <div class="wrapper center">
          <p class="title">Zagreb Airport</p>
        </div>
        <div class="wrapper center">
          <div class="time-column">
            <p class="time-label">Departure Time:</p>
            <p class="card-time">5:30</p>
          </div>
          <div class="time-column">
            <p class="time-label">Arrival Time:</p>
            <p class="card-time">6:30</p>
          </div>
        </div>
        <div class="wrapper">
          <div class="left-section">
            <img src="../../img/driver.svg" alt="Avatar">
            <p class="card-text"> &nbsp;&nbsp;Pedro</p>
          </div>
          <div class="right-section">
            <p>&nbsp;08.06.2023</p>
          </div>
        </div>
      </div>
    </div>
    <div style="margin-bottom: 100px;"></div>

    <banner />
    <navbar />
  </div>
</template>

<style>
.card {
  cursor: pointer;
  width: 100%;
  height: 140px;
  padding: 10px;
  font-family: Nunito;
  border: 1px solid white;
  /* White border */
  border-radius: px;
  margin-top: 20px;
  margin-bottom: 20px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  z-index: 9998;
  color: white;
  /* Set text color to white */
}

.wrapper {
  display: flex;
  justify-content: space-between;
  text-align: center;
  margin-bottom: 5px;
}

.wrapper-driver {
  text-align: left;

}

.card-title {
  color: white;
  font-size: 24px;
  margin-bottom: 10px;
  margin-left: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.time-column {
  flex: 1;
}

.time-label {
  font-family: 'Nunito';
  font-style: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  opacity: 0%;
}

.card-time {
  font-family: 'Nunito';
  font-style: normal;
  margin-bottom: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.card-text {
  font-family: 'Nunito';
  font-style: normal;
  font-size: 16px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.left-section {
  display: flex;
  margin-left: 10px;
}

.right-section {
  margin-left: auto;
  margin-right: 10px;
}

.pink {
  background: linear-gradient(135deg, #A690E0, #CFA7E8);
}

.bg-teal {
  background: linear-gradient(-45deg, #96B8FF, #CFA7E8);
}

.bg-blue {
  background-color: #96B8FF;
}

.grey {
  color: grey;
}

.white {
  color: white;
}

.center {
  display: flex;
  align-items: center;
  justify-content: center;
}

.title {
  font-size: 16px;
  margin-top: 30px;
}
</style>
