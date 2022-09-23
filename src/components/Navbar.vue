
<script setup>
    import { ref } from 'vue'
    const brand = ref ('🏢 Company Directory')
</script>


<template>
    <nav >
        <div class ="wrapper">
            <RouterLink :to="{name: 'Home'}" class="brand">
                <span class="brand-title">{{ brand }}</span>
            </RouterLink>
            <div class = "menu">
                <a href = "#" class="menu-item">Departments</a>
                <a href = "#" class="menu-item">Settings</a>
                <a href = "#" class="menu-login">Logout</a>
            </div>
        </div>
    </nav>
</template>

<style scoped lang="postcss">
    nav {
        @apply flex h-20 bg-amber-200 text-slate-900;
        .wrapper {
            @apply container mx-auto flex w-full items-center justify-between;
            .brand {
                &-title {
                    @apply text-2xl font-bold text-slate-900;
                }
            }
            .menu {
                @apply flex gap-2;

                &-item {
                    @apply rounded-md px-4 py-2 hover:bg-amber-400 hover:text-neutral-100;
                }
                &-login {
                    @apply rounded-md bg-red-700 px-4 py-2 text-red-100 hover:bg-red-900;
                }
            }
        }
    }

</style>