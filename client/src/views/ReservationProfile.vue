<template>
  <!-- Add your reservation profile content here -->
  <SearchBar />
  <div class="min-h-screen flex flex-col items-center justify-center">
    <div class="max-w bg-white p-6 rounded-2xl shadow-lg">
      <div class="p-8 grid gap-8">
        <!-- Info -->
        <div class="">
          <h2 class="text-3xl text-blue-500 font-mono font-bold">
            #9012948492
          </h2>
          <p class="font-mono">Service: Wrap, Tint</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-20">
          <!-- Contact -->
          <div class="text-center">
            <h3 class="text-2xl text-blue-500 font-mono">Contact</h3>
            <p class="font-mono">Name: Hassan Animashaun</p>
            <p class="font-mono">Email: test123@gmail.com</p>
            <p class="font-mono">Phone: 9105274574</p>
          </div>
          <!-- Vehicle -->
          <div class="text-center">
            <h3 class="text-2xl text-blue-500 font-mono">Vehicle</h3>
            <p class="font-mono">Year: 1999</p>
            <p class="font-mono">Make: Honda</p>
            <p class="font-mono">Model: Civic</p>
            <p class="font-mono">Color: Silver</p>
          </div>
        </div>

        <div class="grid grid-col-1 md:grid-cols-1 gap-8">
          <!-- Description -->
          <div>
            <h3 class="text-2xl text-blue-500 font-mono text-center">
              Description
            </h3>
            <p class="font-mono mt-2 text-left text-balance">
              Is simply dummy text of the printing and typesetting industry.
              Lorem is simply dummy text of the printing and typesetting
              industry.Is simply dummy text of the printing and typesetting
              industry. Lorem is simply dummy text of the printing and
              typesetting industry.Is simply dummy text of the printing and
              typesetting industry. Lorem is simply dummy text of the printing
              and typesetting industry.
            </p>
          </div>

          <!-- Photos -->
          <div>
            <h3 class="text-2xl text-blue-500 font-mono text-center">Photos</h3>
            <!-- Replace with actual photos -->
            <div class="w-32 h-32 bg-gray-200 mt-4 rounded"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from '@/components/SearchBar.vue';
import api from '@/services/Api';

export default {
  name: 'ReservationProfile',
  components: { SearchBar },
  data() {
    return {
      // Add your component data here
    };
  },
  methods: {
    // Add your component methods here
  },
  async mounted() {
    const token = localStorage.getItem('token');
    if (!token) {
      this.$router.push('/login');
      return;
    }

    try {
      const axiosInstance = api(token);
      const response = await axiosInstance.get('/reservations');
      console.log(response.data);
    } catch (error) {
      console.log(error);
      localStorage.removeItem('token');
      this.$router.push('/login');
    }
  },
};
</script>

<style scoped>
.reservation-profile {
  padding: 2rem;
}
</style>
