<template>
    <div>
        <nav>
            <div class="sticky top-0 z-40">
                <div
                    class="w-full h-20 px-6 border-b flex items-center justify-between"
                >
                    <!-- left navbar -->
                    <div class="flex">
                        <!-- mobile hamburger -->
                        <div class="flex items-center mr-4 lg:hidden inline-block">
                            <button @click="showingNavigationDropdown = !showingNavigationDropdown" class="inline-flex items-center justify-center p-2 rounded-md text-gray-700 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 focus:text-gray-500 transition">
                                <svg class="h-6 w-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                                    <path :class="{'hidden': showingNavigationDropdown, 'inline-flex': !showingNavigationDropdown }" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                                    <path :class="{'hidden': !showingNavigationDropdown, 'inline-flex': showingNavigationDropdown }" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                                </svg>
                            </button>
                        </div>
                    </div>

                    <!-- right navbar -->
                    <div class="flex items-center relative">
                        <jet-dropdown align="right" width="48">
                            <template #trigger>
                                <button v-if="$page.props.jetstream.managesProfilePhotos" class="flex text-sm border-2 border-transparent rounded-full focus:outline-none focus:border-gray-300 transition">
                                    <img class="h-8 w-8 rounded-full object-cover" :src="$page.props.user.profile_photo_url" :alt="$page.props.user.name" />
                                </button>

                                <span v-else class="inline-flex rounded-md">
                                    <button type="button" class="inline-flex items-center px-3 py-2 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-500 hover:text-gray-700 focus:outline-none transition">
                                        {{ $page.props.user.name }}

                                        <svg class="ml-2 -mr-0.5 h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                                            <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
                                        </svg>
                                    </button>
                                </span>
                            </template>

                            <template #content>
                                <!-- Account Management -->
                                <div class="block px-4 py-2 text-xs text-gray-400">
                                    Manage Account
                                </div>

                                <jet-dropdown-link :href="route('profile.show')">
                                    Profile
                                </jet-dropdown-link>

                                <div class="border-t border-gray-100"></div>

                                <!-- Authentication -->
                                <form @submit.prevent="logout">
                                    <jet-dropdown-link as="button">
                                        Log out
                                    </jet-dropdown-link>
                                </form>
                            </template>
                        </jet-dropdown>
                    </div>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>
    import JetDropdown from '@/Jetstream/Dropdown'
    import JetDropdownLink from '@/Jetstream/DropdownLink'

    export default {
        components: {
            JetDropdown,
            JetDropdownLink,
        },
        data() {
            return {
                showingNavigationDropdown: false,
            }
        },
        methods: {
            logout() {
                this.$inertia.post(route('logout'));
            },
        }
    };
</script>
