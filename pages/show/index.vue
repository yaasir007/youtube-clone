<script setup>
import { MenuIcon, YoutubeIcon, SearchIcon, VideoIcon, BellIcon, UserIcon, HomeIcon, CompassIcon, PlayIcon, BookmarkIcon, ThumbsUpIcon, ThumbsDownIcon } from 'lucide-vue-next'

const isSidebarOpen = ref(false)

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}

const sidebarItems = [
  { name: 'Home', icon: HomeIcon, href: '../' },
  { name: 'Explore', icon: CompassIcon, href: '#' },
  { name: 'Subscriptions', icon: PlayIcon, href: '#' },
  { name: 'Library', icon: BookmarkIcon, href: '#' },
]

const currentVideo = ref({
  id: 1,
  videoId: 'Mm2f1ylqhX8',
  title: 'Never Gonna Give You Up',
  channelName: 'Rick Astley',
  channelAvatar: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  subscribers: '2.5M',
  description: 'The official video for "Never Gonna Give You Up" by Rick Astley. Released in 1987, this song became a global hit and has since become an internet phenomenon known as "Rickrolling".',
  views: '1.2B',
  uploadedAt: '14 years ago'
})

const recommendedVideos = ref([
  {
    id: 2,
    title: 'The Science of Rickrolling',
    channelName: 'VSauce',
    thumbnail: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    views: '5.7M',
    uploadedAt: '2 years ago'
  },
  {
    id: 3,
    title: 'History of Memes: Rickroll',
    channelName: 'Internet Historian',
    thumbnail: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    views: '3.2M',
    uploadedAt: '1 year ago'
  },
  {
    id: 4,
    title: '10 Hours of Never Gonna Give You Up',
    channelName: 'Meme Central',
    thumbnail: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    views: '12M',
    uploadedAt: '5 years ago'
  },
  {
    id: 5,
    title: 'Rick Astley Reacts to Rickroll Memes',
    channelName: 'BuzzFeed',
    thumbnail: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    views: '8.9M',
    uploadedAt: '3 months ago'
  },
  {
    id: 6,
    title: 'The Psychology of Internet Pranks',
    channelName: 'TED-Ed',
    thumbnail: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    views: '2.1M',
    uploadedAt: '8 months ago'
  }
])

const comments = ref([
  {
    id: 1,
    username: 'MemeExpert',
    avatar: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    content: 'This song never gets old. Best rickroll ever!',
    timestamp: '2 days ago',
    likes: 1024
  },
  {
    id: 2,
    username: '80sKid',
    avatar: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    content: 'I remember when this first came out. Still a banger!',
    timestamp: '1 week ago',
    likes: 512
  },
  {
    id: 3,
    username: 'NewToInternet',
    avatar: 'https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    content: 'Why does everyone keep sending me this link?',
    timestamp: '3 hours ago',
    likes: 256
  }
])
</script>

<template>
  <div class="min-h-screen bg-gray-900 text-gray-100">
    <!-- Header -->
    <header class="bg-gray-800 shadow-md fixed top-0 left-0 right-0 z-10">
      <div class="w-full mx-auto px-4 sm:px-6 lg:px-8 py-2 flex items-center justify-between">
        <div class="flex items-center">
          <button @click="toggleSidebar" class="p-2 rounded-full hover:bg-gray-700 lg:hidden">
            <MenuIcon class="h-6 w-6 text-gray-300" />
          </button>
          <YoutubeIcon class="h-6 w-6 text-red-500 ml-2 lg:ml-0" />
          <span class="ml-2 text-xl font-semibold hidden sm:inline">YouTube</span>
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
    <aside :class="['fixed left-0 top-14 bottom-0 w-64 bg-gray-800 z-20 transform transition-transform duration-300 ease-in-out lg:translate-x-0', isSidebarOpen ? 'translate-x-0' : '-translate-x-full']">
      <nav class="p-4">
        <ul class="space-y-2">
          <li v-for="item in sidebarItems" :key="item.name">
            <a :href="item.href" class="flex items-center p-2 rounded-lg hover:bg-gray-700 text-gray-300 hover:text-white">
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
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
          <!-- Video Player and Details -->
          <div class="lg:col-span-2">
            <div class="bg-black aspect-w-16 aspect-h-9 mb-4 h-96	">
              <iframe
                :src="'https://www.youtube.com/embed/' + currentVideo.videoId"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen
                class="w-full h-full"
              ></iframe>
            </div>
            <h1 class="text-2xl font-bold mb-2">{{ currentVideo.title }}</h1>
            <div class="flex items-center justify-between mb-4">
              <div class="flex items-center">
                <img :src="currentVideo.channelAvatar" :alt="currentVideo.channelName + ' Avatar'" class="w-10 h-10 rounded-full mr-2" />
                <div>
                  <h2 class="font-semibold">{{ currentVideo.channelName }}</h2>
                  <p class="text-sm text-gray-400">{{ currentVideo.subscribers }} subscribers</p>
                </div>
              </div>
              <button class="bg-red-600 text-white px-4 py-2 rounded-full font-semibold hover:bg-red-700 transition duration-300">
                Subscribe
              </button>
            </div>
            <div class="bg-gray-800 p-4 rounded-lg mb-4">
              <p>{{ currentVideo.description }}</p>
            </div>

            <!-- Comments Section -->
            <div class="mt-8">
              <h3 class="text-xl font-semibold mb-4">Comments</h3>
              <div class="flex items-center mb-4">
                <img src="https://images.unsplash.com/photo-1666615435088-4865bf5ed3fd?q=80&w=2942&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Your Avatar" class="w-10 h-10 rounded-full mr-2" />
                <input
                  type="text"
                  placeholder="Add a comment..."
                  class="flex-grow px-4 py-2 bg-gray-700 border border-gray-600 rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-100 placeholder-gray-400"
                />
              </div>
              <div class="space-y-4">
                <div v-for="comment in comments" :key="comment.id" class="flex space-x-3">
                  <img :src="comment.avatar" :alt="comment.username + ' Avatar'" class="w-10 h-10 rounded-full" />
                  <div>
                    <p class="font-semibold">{{ comment.username }} <span class="text-gray-400 text-sm ml-2">{{ comment.timestamp }}</span></p>
                    <p class="text-gray-300">{{ comment.content }}</p>
                    <div class="flex items-center space-x-2 mt-2">
                      <button class="flex items-center text-gray-400 hover:text-gray-200">
                        <ThumbsUpIcon class="h-4 w-4 mr-1" />
                        {{ comment.likes }}
                      </button>
                      <button class="flex items-center text-gray-400 hover:text-gray-200">
                        <ThumbsDownIcon class="h-4 w-4 mr-1" />
                      </button>
                      <button class="text-gray-400 hover:text-gray-200">Reply</button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Recommended Videos -->
          <div class="space-y-4">
            <h2 class="text-xl font-semibold mb-2">Recommended</h2>
            <div v-for="video in recommendedVideos" :key="video.id" class="flex space-x-2">
              <img :src="video.thumbnail" :alt="video.title" class="w-40 h-24 object-cover rounded" />
              <div>
                <h3 class="font-semibold">{{ video.title }}</h3>
                <p class="text-sm text-gray-400">{{ video.channelName }}</p>
                <p class="text-sm text-gray-500">{{ video.views }} views • {{ video.uploadedAt }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>
