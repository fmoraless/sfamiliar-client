<!--<template>
  <div class="flex flex-col mt-8">
    <div class="overflow-x-auto">
      <div class="flex justify-between py-3 pl-2">
        <h1 class="text-2xl font-bold">Pacientes view</h1>
      </div>
      <div class="p-1.5 w-full inline-block align-middle">
        <div class="overflow-hidden border rounded-lg">
          <table class="min-w-full divide-y divide-gray-200">
            <thead class="bg-gray-50">
              <tr>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-left text-gray-500 uppercase"
                >
                  ID
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-left text-gray-500 uppercase"
                >
                  Nombres
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-left text-gray-500 uppercase"
                >
                  Rut
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-left text-gray-500 uppercase"
                >
                  Ficha
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-left text-gray-500 uppercase"
                >
                  Sector
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-right text-gray-500 uppercase"
                >
                  Edit
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold text-right text-gray-500 uppercase"
                >
                  Delete
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200">
              <tr v-for="patient in displayedPacientes" :key="patient.id">
                <td
                  class="px-6 py-4 text-sm font-medium text-gray-800 whitespace-nowrap"
                >
                  {{ patient.id }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-800 whitespace-nowrap">
                  {{ patient.nombres }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-800 whitespace-nowrap">
                  {{ patient.rut }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-800 whitespace-nowrap">
                  {{ patient.ficha ?? "Sin ficha" }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-800 whitespace-nowrap">
                  {{ patient.sector }}
                </td>
                <td
                  class="px-6 py-4 text-sm font-medium text-right whitespace-nowrap"
                >
                  <a class="text-green-500 hover:text-green-700" href="#">
                    <span>
                      <font-awesome-icon
                        :icon="['fas', 'edit']"
                        class="mr-0.5"
                      />
                    </span>
                  </a>
                </td>
                <td
                  class="px-6 py-4 text-sm font-medium text-right whitespace-nowrap"
                >
                  <a class="text-red-500 hover:text-red-700" href="#">
                    <span>
                      <font-awesome-icon
                        :icon="['fas', 'trash-alt']"
                        class="mr-0.5"
                      />
                    </span>
                  </a>
                </td>
              </tr>
            </tbody>
          </table>
          <div class="mt-8 mx-auto">
            <div class="flex flex-row flex-nowrap">
              <p class="text-sm flex-grow">Página {{ currentPage }}</p>
              <div class="flex items-center justify-center">
                <router-link
                  v-if="previousPage"
                  :to="{ name: 'Patients', query: { page: previousPage } }"
                  class="mx-3 text-sm font-semibold text-brand-blue-1"
                >
                  Anterior
                </router-link>
                <router-link
                  v-if="nextPage"
                  :to="{ name: 'Patients', query: { page: nextPage } }"
                  class="mx-3 text-sm font-semibold text-brand-blue-1"
                >
                  Siguiente
                </router-link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>-->
<template>
  <div class="q-pa-md">
    <q-toggle v-model="loading" label="Loading state" class="q-mb-md" />
    <q-table
      title="Pacientes"
      :rows="rows"
      :columns="columns"
      color="primary"
      row-key="name"
      :loading="loading"
    >
      <template v-slot:loading>
        <q-inner-loading showing color="primary" />
      </template>
    </q-table>
  </div>
</template>
<script>
//import axios from "axios";

import { ref } from "vue";

const columns = [
  {
    name: "name",
    required: true,
    label: "Rut",
    align: "left",
    field: (row) => row.name,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "calories",
    align: "center",
    label: "Nombres",
    field: "calories",
    sortable: true,
  },
  { name: "fat", label: "Fat (g)", field: "fat", sortable: true },
  { name: "carbs", label: "Carbs (g)", field: "carbs" },
  { name: "protein", label: "Protein (g)", field: "protein" },
  { name: "sodium", label: "Sodium (mg)", field: "sodium" },
  {
    name: "calcium",
    label: "Calcium (%)",
    field: "calcium",
    sortable: true,
    sort: (a, b) => parseInt(a, 10) - parseInt(b, 10),
  },
  {
    name: "iron",
    label: "Iron (%)",
    field: "iron",
    sortable: true,
    sort: (a, b) => parseInt(a, 10) - parseInt(b, 10),
  },
];

const rows = [
  {
    name: "19200398-7",
    calories: "JUAN MIGUEL TORO MENDEZ",
    fat: 6.0,
    carbs: 24,
    protein: 4.0,
    sodium: 87,
    calcium: "14%",
    iron: "1%",
  },
  {
    name: "16990879-K",
    calories: "MATIAS FERREIRA GONZALEZ",
    fat: 9.0,
    carbs: 37,
    protein: 4.3,
    sodium: 129,
    calcium: "8%",
    iron: "1%",
  },
  {
    name: "21908567-K",
    calories: "CAROLINA GONZALEZ GONZALEZ",
    fat: 16.0,
    carbs: 23,
    protein: 6.0,
    sodium: 337,
    calcium: "6%",
    iron: "7%",
  },
  {
    name: "55908123-2",
    calories: "ARTURO GOYCOOLEA SHARP",
    fat: 3.7,
    carbs: 67,
    protein: 4.3,
    sodium: 413,
    calcium: "3%",
    iron: "8%",
  },
  {
    name: "23562779-8",
    calories: "MARCELO CIFUENTES",
    fat: 16.0,
    carbs: 49,
    protein: 3.9,
    sodium: 327,
    calcium: "7%",
    iron: "16%",
  },
  {
    name: "18980672-0",
    calories: "MARIBEL PUEBLA",
    fat: 0.0,
    carbs: 94,
    protein: 0.0,
    sodium: 50,
    calcium: "0%",
    iron: "0%",
  },
  {
    name: "18980672-0",
    calories: "JOAQUIN CORREA",
    fat: 0.2,
    carbs: 98,
    protein: 0,
    sodium: 38,
    calcium: "0%",
    iron: "2%",
  },
  {
    name: "18980672-0",
    calories: "EDUARDO MONREAL",
    fat: 3.2,
    carbs: 87,
    protein: 6.5,
    sodium: 562,
    calcium: "0%",
    iron: "45%",
  },
  {
    name: "8945688-2",
    calories: "ROJELIO ROJAS",
    fat: 25.0,
    carbs: 51,
    protein: 4.9,
    sodium: 326,
    calcium: "2%",
    iron: "22%",
  },
  {
    name: "26518794-5",
    calories: "PAMELA RIOS",
    fat: 26.0,
    carbs: 65,
    protein: 7,
    sodium: 54,
    calcium: "12%",
    iron: "6%",
  },
];

export default {
  setup() {
    return {
      loading: ref(false),
      columns,
      rows,
    };
  },
};
/*export default {
  name: "PatientsView",
  data() {
    return {
      patients: [],
    };
  },
  computed: {
    currentPage() {
      const pageString = this.$route.query.page || "1";
      console.log(pageString);
      return Number.parseInt(pageString);
    },
    previousPage() {
      const previousPage = this.currentPage - 1; // 1 - 1 = 0  - || 2 - 1 = 1
      const firstPage = 1;
      return previousPage >= firstPage ? previousPage : undefined;
    },
    nextPage() {
      const nextPage = this.currentPage + 1;
      const maxPage = this.patients.length / 10; // 100/ 10 = 10
      return nextPage <= maxPage ? nextPage : undefined;
    },
    displayedPacientes() {
      const pageNumber = this.currentPage;
      const firstPatIndex = (pageNumber - 1) * 10; // 1 -1 = 0 * 10 = 0
      const lastPatIndex = pageNumber * 10;
      return this.patients.slice(firstPatIndex, lastPatIndex);
    },
  },
  async mounted() {
    const response = await axios.get("http://127.0.0.1:8000/api/v1/pacientes/");
    this.patients = response.data.data;
    console.log(this.patients, "patients");
  },
};*/
</script>
