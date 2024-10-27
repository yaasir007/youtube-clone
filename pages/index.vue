<script setup>
import { ref, computed } from "vue";
import {
  MenuIcon,
  YoutubeIcon,
  SearchIcon,
  VideoIcon,
  BellIcon,
  UserIcon,
  HomeIcon,
  CompassIcon,
  PlayIcon,
  BookmarkIcon,
} from "lucide-vue-next";

const isSidebarOpen = ref(false);
const selectedCategory = ref("All");

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};

const selectCategory = (category) => {
  selectedCategory.value = category;
};

const sidebarItems = [
  { name: "Home", icon: HomeIcon, href: "#" },
  { name: "Explore", icon: CompassIcon, href: "#" },
  { name: "Subscriptions", icon: PlayIcon, href: "#" },
  { name: "Library", icon: BookmarkIcon, href: "#" },
];

const categories = [
  "All",
  "Music",
  "Gaming",
  "News",
  "Live",
  "Sports",
  "Learning",
  "Fashion & Beauty",
  "Comedy",
];

const allVideos = [
  {
    id: 1,
    title: "Vue 3 Crash Course: Learn the Composition API",
    channelName: "Vue Mastery",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "250K",
    uploadedAt: "2 weeks ago",
    category: "Learning",
  },
  {
    id: 2,
    title: "Learn Tailwind CSS in 20 Minutes: A Comprehensive Guide",
    channelName: "Dev Ed",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "500K",
    uploadedAt: "1 month ago",
    category: "Learning",
  },
  {
    id: 3,
    title: "Building a YouTube Clone with Vue 3 and Tailwind CSS",
    channelName: "Coding Garden",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "100K",
    uploadedAt: "3 days ago",
    category: "Learning",
  },
  {
    id: 4,
    title: "Top 10 Video Game Soundtracks of All Time",
    channelName: "Game Music Channel",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "750K",
    uploadedAt: "2 months ago",
    category: "Music",
  },
  {
    id: 5,
    title: "Live Concert: Electronic Music Festival 2023",
    channelName: "EDM Lovers",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "1M",
    uploadedAt: "6 months ago",
    category: "Music",
  },
  {
    id: 6,
    title: "Minecraft Speedrun World Record Attempt",
    channelName: "Pro Gamer",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "300K",
    uploadedAt: "3 weeks ago",
    category: "Gaming",
  },
  {
    id: 7,
    title: "Fortnite Chapter 4 Season 3: What to Expect",
    channelName: "Fortnite Central",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "450K",
    uploadedAt: "1 month ago",
    category: "Gaming",
  },
  {
    id: 8,
    title: "Breaking News: Major Tech Company Announces Revolutionary AI",
    channelName: "Tech News Now",
    thumbnail:
      "https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    views: "2M",
    uploadedAt: "4 months ago",
    category: "News",
  },
];

const filteredVideos = computed(() => {
  if (selectedCategory.value === "All") {
    return allVideos;
  } else {
    return allVideos.filter(
      (video) => video.category === selectedCategory.value
    );
  }
});
</script>

<template>
  <div class="min-h-screen bg-gray-900 text-gray-100">
    <!-- Header -->
    <header class="bg-gray-800 shadow-md fixed top-0 left-0 right-0 z-10">
      <div
        class="w-full mx-auto px-4 sm:px-6 lg:px-8 py-2 flex items-center justify-between"
      >
        <div class="flex items-center">
          <button
            @click="toggleSidebar"
            class="p-2 rounded-full hover:bg-gray-700 lg:hidden"
          >
            <MenuIcon class="h-6 w-6 text-gray-300" />
          </button>
          <YoutubeIcon class="h-6 w-6 text-red-500 ml-2 lg:ml-0" />
          <span class="ml-2 text-xl font-semibold hidden sm:inline"
            >YouTube</span
          >
        </div>
        <div class="flex-1 max-w-xl mx-4 hidden sm:block">
          <div class="relative">
            <input
              type="text"
              placeholder="Search"
              class="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-100 placeholder-gray-400"
            />
            <button class="absolute right-0 top-0 mt-2 mr-4">
              <SearchIcon class="h-5 w-5 text-gray-400" />
            </button>
          </div>
        </div>
        <div class="flex items-center">
          <button class="p-2 rounded-full hover:bg-gray-700 sm:hidden">
            <SearchIcon class="h-6 w-6 text-gray-300" />
          </button>
          <button class="p-2 rounded-full hover:bg-gray-700 hidden sm:block">
            <VideoIcon class="h-6 w-6 text-gray-300" />
          </button>
          <button class="p-2 rounded-full hover:bg-gray-700">
            <BellIcon class="h-6 w-6 text-gray-300" />
          </button>
          <button class="p-2 rounded-full hover:bg-gray-700">
            <UserIcon class="h-6 w-6 text-gray-300" />
          </button>
        </div>
      </div>
    </header>

    <!-- Sidebar -->
    <aside
      :class="[
        'fixed left-0 top-14 bottom-0 w-64 bg-gray-800 z-20 transform transition-transform duration-300 ease-in-out lg:translate-x-0',
        isSidebarOpen ? 'translate-x-0' : '-translate-x-full',
      ]"
    >
      <nav class="p-4">
        <ul class="space-y-2">
          <li v-for="item in sidebarItems" :key="item.name">
            <a
              :href="item.href"
              class="flex items-center p-2 rounded-lg hover:bg-gray-700 text-gray-300 hover:text-white"
            >
              <component :is="item.icon" class="h-5 w-5 mr-3" />
              <span>{{ item.name }}</span>
            </a>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="pt-16 lg:pl-64">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <!-- Categories -->
        <div class="flex space-x-4 overflow-x-auto pb-4 scrollbar-hide">
          <button
            v-for="category in categories"
            :key="category"
            :class="[
              'px-3 py-1 text-xs sm:px-4 sm:py-2 sm:text-sm rounded-full font-medium whitespace-nowrap',
              category === selectedCategory
                ? 'bg-white text-black'
                : 'bg-gray-700 text-gray-300 hover:bg-gray-600',
            ]"
            @click="selectCategory(category)"
          >
            {{ category }}
          </button>
        </div>

        <!-- Video Grid -->
        <transition-group
          name="video-fade"
          tag="div"
          class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4 mt-8"
        >
          <div
            v-for="video in filteredVideos"
            :key="video.id"
            class="bg-gray-800 rounded-lg shadow-md overflow-hidden"
          >
            <NuxtLink to="./show">
              <img
                :src="video.thumbnail"
                :alt="video.title"
                class="w-full h-48 object-cover"
              />
              <div class="p-4">
                <h3
                  class="font-semibold text-base sm:text-lg mb-2 text-gray-100 line-clamp-2"
                >
                  {{ video.title }}
                </h3>
                <p class="text-gray-400 text-sm">{{ video.channelName }}</p>
                <p class="text-gray-500 text-xs mt-1">
                  {{ video.views }} views • {{ video.uploadedAt }}
                </p>
              </div>
            </NuxtLink>
          </div>
        </transition-group>
      </div>
    </main>
  </div>
</template>

<style scoped>
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.video-fade-move,
.video-fade-enter-active,
.video-fade-leave-active {
  transition: all 0.5s ease;
}

.video-fade-enter-from,
.video-fade-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.video-fade-leave-active {
  position: absolute;
}
</style>
