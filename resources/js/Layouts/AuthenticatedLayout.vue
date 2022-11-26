<script setup>
import { ref } from 'vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/inertia-vue3';
import { Navbar,Dropdown,ListGroup, ListGroupItem, NavbarLogo, NavbarCollapse, NavbarLink } from 'flowbite-vue'
const showingNavigationDropdown = ref(false);
</script>

<template>
    <div>
        <Navbar>
            <template #logo>
            <NavbarLogo :link="route('dashboard')" alt="Flowbite logo" image-url="https://flowbite.com/docs/images/logo.svg">
                Flowbite
            </NavbarLogo>
            </template>
            <template #default="{isShowMenu}">
            <NavbarCollapse :isShowMenu="isShowMenu">
                <NavbarLink isActive :link="route('dashboard')">Home</NavbarLink>
                <NavbarLink link="#">Inicio</NavbarLink>
                <NavbarLink link="#">Pacientes</NavbarLink>
                <NavbarLink link="#">Consentimientos</NavbarLink>
                <dropdown placement="bottom" :text="$page.props.auth.user.name">
                    <list-group>
                        <list-group-item>
                            <template #prefix>
                            <svg class="w-4 h-4 fill-current" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-6-3a2 2 0 11-4 0 2 2 0 014 0zm-2 4a5 5 0 00-4.546 2.916A5.986 5.986 0 0010 16a5.986 5.986 0 004.546-2.084A5 5 0 0010 11z" clip-rule="evenodd"></path></svg>
                            </template>
                            <a :href="route('profile.edit')">Perfil</a>
                        </list-group-item>
                        <list-group-item>
                            <template #prefix>
                                X
                            </template>
                            <a :href="route('logout')">Log out</a>
                        </list-group-item>
                    </list-group>
                </dropdown>
            </NavbarCollapse>
            </template>
        </Navbar>
           <!-- Page Heading -->
        <header class="bg-white shadow" v-if="$slots.header">
            <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                <slot name="header" />
            </div>
        </header>

            <!-- Page Content -->
        <main>
            <slot />
        </main>
    </div>
</template>
