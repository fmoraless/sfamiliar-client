<template>
  <header class="w-full text-sm">
    <div class="fixed top-0 left-0 w-full h-16 bg-white">
      <div
        class="flex flex-nowrap h-full px-8 mx-auto border-b border-solid border-brand-gray-1"
      >
        <router-link
          :to="{ name: 'Home' }"
          class="flex items-center h-full text-xl"
          >AppTitle
        </router-link>
        <nav class="h-full ml-12">
          <ul class="flex h-full p-0 m-0 list-none">
            <li
              v-for="menuItem in menuItems"
              :key="menuItem.text"
              class="h-full ml-9 first:ml-0"
            >
              <router-link
                :to="menuItem.url"
                class="flex items-center h-full py-2.5"
                ><span>
                  <font-awesome-icon :icon="menuItem.icon" class="mr-0.5" />
                  {{ menuItem.text }}
                </span>
              </router-link>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "MainNav",
  data() {
    return {
      menuItems: [
        { text: "Pacientes", url: "/patients", icon: ["fas", "users"] },
        { text: "Familias", url: "/familias", icon: ["fa", "people-group"] },
        { text: "Viviendas", url: "/", icon: ["fas", "house-user"] },
        { text: "Factores", url: "/", icon: ["fas", "calculator"] },
        { text: "Reportes", url: "/", icon: ["fas", "chart-line"] },
      ],
    };
  },
};
</script>

<style scoped></style>
