<!-- dashboard/email-marketing.vue -->
<template>
    <!-- Added overflow-x-hidden to prevent horizontal scrolling -->
    <div class="min-h-screen bg-gray-50 dark:bg-slate-950 transition-colors duration-300 p-4 sm:p-6 overflow-x-hidden">
        <!-- Header -->
        <div class="mb-8">
            <h1 class="text-2xl sm:text-3xl font-bold text-gray-900 dark:text-white">Email Marketing</h1>
            <p class="text-sm sm:text-base text-gray-600 dark:text-gray-400 mt-2">
                Create, manage, and analyze your email campaigns
            </p>
        </div>

        <!-- Quick Stats -->
        <div class="grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-4 gap-4 mb-8">
            <div class="bg-white dark:bg-slate-900 rounded-xl shadow-sm dark:shadow-none border border-gray-100 dark:border-slate-800 p-5 transition-colors">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Total Lists</p>
                        <p class="text-2xl font-bold text-gray-900 dark:text-white mt-1">{{ emailStore.lists.length }}</p>
                    </div>
                    <div class="p-3 bg-blue-100 dark:bg-blue-900/30 rounded-lg">
                        <svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
                        </svg>
                    </div>
                </div>
            </div>

            <div class="bg-white dark:bg-slate-900 rounded-xl shadow-sm dark:shadow-none border border-gray-100 dark:border-slate-800 p-5 transition-colors">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Total Contacts</p>
                        <p class="text-2xl font-bold text-gray-900 dark:text-white mt-1">{{ totalContacts }}</p>
                    </div>
                    <div class="p-3 bg-green-100 dark:bg-green-900/30 rounded-lg">
                        <svg class="w-6 h-6 text-green-600 dark:text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
                        </svg>
                    </div>
                </div>
            </div>

            <div class="bg-white dark:bg-slate-900 rounded-xl shadow-sm dark:shadow-none border border-gray-100 dark:border-slate-800 p-5 transition-colors">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Templates</p>
                        <p class="text-2xl font-bold text-gray-900 dark:text-white mt-1">{{ emailStore.templateStats.my_templates }}</p>
                    </div>
                    <div class="p-3 bg-purple-100 dark:bg-purple-900/30 rounded-lg">
                        <svg class="w-6 h-6 text-purple-600 dark:text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 5a1 1 0 011-1h14a1 1 0 011 1v2a1 1 0 01-1 1H5a1 1 0 01-1-1V5zM4 13a1 1 0 011-1h6a1 1 0 011 1v6a1 1 0 01-1 1H5a1 1 0 01-1-1v-6zM16 13a1 1 0 011-1h2a1 1 0 011 1v6a1 1 0 01-1 1h-2a1 1 0 01-1-1v-6z" />
                        </svg>
                    </div>
                </div>
            </div>

            <div class="bg-white dark:bg-slate-900 rounded-xl shadow-sm dark:shadow-none border border-gray-100 dark:border-slate-800 p-5 transition-colors">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Campaigns</p>
                        <p class="text-2xl font-bold text-gray-900 dark:text-white mt-1">{{ emailStore.campaigns.length }}</p>
                    </div>
                    <div class="p-3 bg-orange-100 dark:bg-orange-900/30 rounded-lg">
                        <svg class="w-6 h-6 text-orange-600 dark:text-orange-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                        </svg>
                    </div>
                </div>
            </div>
        </div>

        <!-- Navigation Tabs -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow-sm dark:shadow-none border border-gray-200 dark:border-slate-800 mb-6 transition-colors overflow-hidden">
            <!-- Added scrollbar-hide and max-w-full to prevent tab overflow -->
            <div class="border-b border-gray-200 dark:border-slate-800 overflow-x-auto scrollbar-hide max-w-full">
                <nav class="flex -mb-px min-w-full">
                    <button v-for="tab in tabs" :key="tab.id" @click="activeTab = tab.id" :class="[
                        'px-6 py-4 text-sm font-medium border-b-2 transition-colors whitespace-nowrap flex-1 text-center',
                        activeTab === tab.id
                            ? 'border-purple-600 text-purple-600 dark:text-purple-400'
                            : 'border-transparent text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white hover:border-gray-300 dark:hover:border-slate-600'
                    ]">
                        {{ tab.label }}
                    </button>
                </nav>
            </div>

            <!-- Tab Content -->
            <div class="p-4 sm:p-6">
                <component :is="activeTabComponent" />
            </div>
        </div>

        <!-- Notifications Portal (Same as before) -->
        <teleport to="body">
            <div v-if="notifications.length > 0" class="fixed bottom-4 right-4 space-y-2 z-50 w-full max-w-[calc(100vw-2rem)] px-4 sm:px-0 sm:w-auto">
                <transition-group name="slide-fade">
                    <div v-for="notification in notifications" :key="notification.id"
                        class="bg-white dark:bg-slate-800 rounded-lg shadow-lg p-4 border-l-4 border-purple-600 dark:border-purple-500 flex items-start gap-3">
                        <!-- Notification content (same as before) -->
                        <div class="flex-shrink-0">
                             <svg v-if="notification.type === 'success'" class="w-6 h-6 text-green-500" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
                             <svg v-else class="w-6 h-6 text-blue-500" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z" clip-rule="evenodd"/></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <p class="text-sm font-medium text-gray-900 dark:text-white truncate">{{ notification.title }}</p>
                            <p class="text-sm text-gray-600 dark:text-gray-300 mt-1 break-words">{{ notification.message }}</p>
                        </div>
                        <button @click="removeNotification(notification.id)" class="text-gray-400 hover:text-gray-600">×</button>
                    </div>
                </transition-group>
            </div>
        </teleport>
    </div>
</template>

<script setup>
definePageMeta({ layout: 'dashboard' })
import { ref, computed, onMounted, onUnmounted } from 'vue'
import EmailListsTab from '~/components/emailMarketing/EmailListsTab.vue'
import EmailContactsTab from '~/components/emailMarketing/EmailContactsTab.vue'
import EmailTemplatesTab from '~/components/emailMarketing/EmailTemplatesTab.vue'
import EmailCampaignsTab from '~/components/emailMarketing/EmailCampaignsTab.vue'
import { useToast } from 'vue-toastification'

const emailStore = useEmailMarketingStore()
const websocketStore = useWebSocketStore()
const $toast = useToast()

const activeTab = ref('campaigns')
const notifications = ref([])

const tabs = [
    { id: 'campaigns', label: 'Campaigns' },
    { id: 'templates', label: 'Templates' },
    { id: 'contacts', label: 'Contacts' },
    { id: 'lists', label: 'Lists' }
]

const activeTabComponent = computed(() => {
    switch (activeTab.value) {
        case 'campaigns': return EmailCampaignsTab
        case 'templates': return EmailTemplatesTab
        case 'contacts': return EmailContactsTab
        case 'lists': return EmailListsTab
        default: return EmailCampaignsTab
    }
})

const totalContacts = computed(() => emailStore.lists.reduce((sum, list) => sum + (list.total_subscribers || 0), 0))

// WebSocket logic remains same...
const setupWebSocketListeners = () => { /* ... */ }
const addNotification = (n) => { notifications.value.push({ id: Date.now(), ...n }); setTimeout(() => removeNotification(n.id), 5000) }
const removeNotification = (id) => { notifications.value = notifications.value.filter(n => n.id !== id) }

onMounted(async () => {
    if (!websocketStore.connected) websocketStore.initialize()
    await Promise.all([
        emailStore.fetchLists(),
        emailStore.fetchTemplates(),
        emailStore.fetchCampaigns(),
        emailStore.fetchTemplateCategories(),
        emailStore.fetchTemplateTags()
    ])
})
</script>

<style scoped>
.scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }
.scrollbar-hide::-webkit-scrollbar { display: none; }
.slide-fade-enter-active { transition: all 0.3s ease; }
.slide-fade-enter-from, .slide-fade-leave-to { transform: translateX(30px); opacity: 0; }
</style>