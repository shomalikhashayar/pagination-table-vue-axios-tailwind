<template>
  <h1 id="header">{{ messageFromKhashayar }}</h1>
  <div class="flex flex-col">
    <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="py-4 inline-block min-w-full sm:px-6 lg:px-8">
        <div class="overflow-hidden">
          <table class="min-w-full text-center">
            <thead class="border-b bg-gray-800">
              <tr>
                <th
                  scope="col"
                  class="text-sm font-medium text-gray-900 text-white px-6 py-4"
                >
                  #
                </th>
                <th
                  scope="col"
                  class="text-sm font-medium text-gray-900 text-white px-6 py-4"
                >
                  First Name
                </th>
                <th
                  scope="col"
                  class="text-sm font-medium text-gray-900 text-white px-6 py-4"
                >
                  Last Name
                </th>
                <th
                  scope="col"
                  class="text-sm font-medium text-gray-900 text-white px-6 py-4"
                >
                  Email
                </th>
                <th
                  scope="col"
                  class="text-sm font-medium text-gray-900 text-white px-6 py-4"
                >
                  Profile
                </th>
              </tr>
            </thead>
            <tbody>
              <tr
                class="border-b"
                v-for="item in usersList"
                v-bind:key="item.id"
              >
                <td
                  class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"
                >
                  {{ item.id }}
                </td>
                <td
                  class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap"
                >
                  {{ item.first_name }}
                </td>
                <td
                  class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap"
                >
                  {{ item.last_name }}
                </td>
                <td
                  class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap"
                >
                  {{ item.email }}
                </td>
                <td
                  class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap"
                >
                  <!-- {{item.avatar}} -->
                  <img
                    id="avatar"
                    :src="item.avatar"
                    alt=""
                    width="45"
                    class="rounded-full"
                  />
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
    <div id="pagination">
      <div class="flex justify-center">
        <nav aria-label="Page navigation example">
          <ul class="flex list-style-none">
            <li class="page-item disabled">
              <a
                class="page-link relative block py-1.5 px-3 border-0 bg-transparent outline-none transition-all duration-300 rounded-full text-gray-500 pointer-events-none focus:shadow-none"
                href="#"
                tabindex="-1"
                aria-disabled="true"
                >Previous</a
              >
            </li>
            <li class="page-item active">
              <a
                class="page-link relative block py-1.5 px-3 border-0 bg-zinc-500 outline-none transition-all duration-300 rounded-full text-white hover:text-white hover:bg-black shadow-md focus:shadow-md"
                href="#"
                >1 (current)<span class="visually-hidden"></span
              ></a>
            </li>
            <li class="page-item">
              <a
                class="page-link relative block py-1.5 px-3 border-0 bg-transparent outline-none transition-all duration-300 rounded-full text-gray-800 hover:text-gray-800 hover:bg-gray-200 focus:shadow-none"
                href="#"
                >2</a
              >
            </li>
            <li class="page-item">
              <a
                class="page-link relative block py-1.5 px-3 border-0 bg-transparent outline-none transition-all duration-300 rounded-full text-gray-800 hover:text-gray-800 hover:bg-gray-200 focus:shadow-none"
                href="#"
                >3</a
              >
            </li>
            <li class="page-item">
              <a
                class="page-link relative block py-1.5 px-3 border-0 bg-transparent outline-none transition-all duration-300 rounded-full text-gray-800 hover:text-gray-800 hover:bg-gray-200 focus:shadow-none"
                href="#"
                >Next</a
              >
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

//API => https://reqres.in/api/users?page=1"

const url = "https://reqres.in/api/users?page=1";

export default {
  data() {
    return {
      usersList: [],
      messageFromKhashayar:
        "... I used Axios library to fetch data from API to my table ...",
      waterMark: "Khashayar Shomali",
    };
  },
  mounted() {
    axios.get(url).then((res) => {
      this.usersList = res.data.data;
      console.log(res.data.data);
      console.log(this.waterMark);
    });
  },
};
</script>

<style>
body {
  overflow-x: hidden;
  background-color: rgb(254, 254, 254);
  padding-left: 20px;
  padding-right: 20px;
}
td {
  background-color: white;
}
#header {
  text-align: center;
  font-size: 22px;
  font-weight: bold;
  margin-top: 1.5em;
  margin-bottom: 0.5em;
}
#avatar {
  margin: 0 auto;
}
img {
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
}
#pagination {
  margin-top: 5px;
  margin-bottom: 20px;
}
</style>
