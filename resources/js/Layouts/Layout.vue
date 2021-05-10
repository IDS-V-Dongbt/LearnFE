<template>
    <div class="min-h-screen">
        <div id="main-body" class="leading-normal tracking-normal">
            <div
                id="main-nav"
                class="w-1/2 md:w-1/3 lg:w-64 fixed md:top-0 md:left-0 h-screen lg:block border-r z-30"
                :class="sideBarOpen ? '' : 'hidden'">
                <admin-side-bar />
            </div>

            <!-- Page body -->
            <div
                id="main-content"
                class="flex flex-col h-screen w-full pl-0 lg:pl-64"
                :class="sideBarOpen ? 'overlay' : ''"
            >
                <admin-nav-bar />
                <div class="p-8 mb-auto">
                    <main class="text-gray-600">
                        <!-- Breadcrumb -->
                        <!-- Breadcrumb end -->

                        <!-- Heading -->
                        <header class="lg:flex justify-between items-center mb-6 text-gray-700" v-if="$slots.header">
                            <p class="text-2xl font-semibold mb-2 lg:mb-0">
                                <slot name="header"></slot>
                            </p>
                        </header>
                        <!-- Heading end -->

                        <!-- Content -->
                        <slot></slot>
                    </main>
                </div>
                <admin-footer />
            </div>
            <!-- Page body end -->
        </div>
    </div>
</template>

<script>
import AdminNavBar from "@/Layouts/NavBar";
import AdminSideBar from "@/Layouts/SideBar";
import AdminFooter from "@/Layouts/Footer";
export default {
    components: {
        AdminNavBar,
        AdminSideBar,
        AdminFooter,
    },
    data() {
        return {
            sideBarOpen: false
        };
    }
};
</script>
