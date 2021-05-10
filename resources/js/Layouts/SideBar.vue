<template>
    <!-- give the sidebar z-50 class so its higher than the navbar if you want to see the logo -->
    <!-- you will need to add a little "X" button next to the logo in order to close it though -->
    <div>
        <div class="w-full h-20 border-b flex px-4 items-center mb-8">
            <p class="font-bold text-3xl pl-4 border-gray-500 text-gray-500">LOGO</p>
        </div>

        <div class="mb-4 px-4">
            <p class="pl-4 text-sm font-semibold mb-1 text-gray-400">MAIN</p>

            <jet-responsive-nav-link :href="route('dashboard')" :active="currentRoute.startsWith('dashboard')">
                <span>Dashboard</span>
            </jet-responsive-nav-link>

            <jet-responsive-nav-link :href="route('posts.index')" :active="currentRoute.startsWith('posts')">
                <span>Posts</span>
            </jet-responsive-nav-link>
        </div>

        <div class="mb-4 px-4">
            <p class="pl-4 text-sm font-semibold mb-1 text-gray-400">MISC</p>

            <jet-responsive-nav-link :href="route('dashboard')">
                <span>Settings </span>
            </jet-responsive-nav-link>
        </div>
    </div>
</template>

<script>
    import JetResponsiveNavLink from '@/Jetstream/ResponsiveNavLink'
    export default {
        components: {
            JetResponsiveNavLink,
        },
        data() {
            return {
                sideBarOpen: false,
                currentRoute: route().current(),
            };
        }
    };
</script>
