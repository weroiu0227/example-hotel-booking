<template>

<v-data-table
    :headers="headers"
    :items="guestManagementPage"
    :items-per-page="5"
    class="elevation-1"
  ></v-data-table>

</template>

<script>
  const axios = require('axios').default;

  export default {
    name: 'GuestManagementPage',
    props: {
      value: Object,
      editMode: Boolean,
      isNew: Boolean
    },
    data: () => ({
        headers: [
            { text: "id", value: "id" },
            { text: "bookId", value: "bookId" },
            { text: "hostId", value: "hostId" },
            { text: "price", value: "price" },
            { text: "startDate", value: "startDate" },
            { text: "endDate", value: "endDate" },
            { text: "roomId", value: "roomId" },
            { text: "status", value: "status" },
            { text: "payId", value: "payId" },
            { text: "hotelId", value: "hotelId" },
        ],
        guestManagementPage : [],
    }),
    async created() {
      var temp = await axios.get(axios.backend + '/guestmanagementpages')

      this.guestManagementPage = temp.data._embedded.guestmanagementpages;

    },
    methods: {
    }
  }
</script>

