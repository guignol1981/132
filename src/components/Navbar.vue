<!-- This example requires Tailwind CSS v2.0+ -->
<template>
    <Disclosure as="nav" class="bg-gray-800" v-slot="{ open }">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex">
                    <div class="-ml-2 mr-2 flex items-center md:hidden">
                        <!-- Mobile menu button -->
                        <DisclosureButton
                            class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
                        >
                            <span class="sr-only">Open main menu</span>
                            <MenuIcon
                                v-if="!open"
                                class="block h-6 w-6"
                                aria-hidden="true"
                            />
                            <XIcon
                                v-else
                                class="block h-6 w-6"
                                aria-hidden="true"
                            />
                        </DisclosureButton>
                    </div>
                    <div class="flex-shrink-0 flex items-center">
                        <img
                            class="block lg:hidden h-8 w-auto"
                            src="@/assets/logo.png"
                            alt="Workflow"
                        />
                        <img
                            class="hidden lg:block h-8 w-auto"
                            src="@/assets/logo.png"
                            alt="Workflow"
                        />
                    </div>
                    <div
                        class="hidden md:ml-6 md:flex md:items-center md:space-x-4"
                    >
                        <a
                            v-for="item in navigation"
                            :key="item.name"
                            href="#"
                            :class="[
                                item.current
                                    ? 'bg-gray-900 text-white'
                                    : 'text-gray-300 hover:bg-gray-700 hover:text-white',
                                'px-3 py-2 rounded-md text-sm font-medium',
                            ]"
                            :aria-current="item.current ? 'page' : undefined"
                            @click.prevent="
                                $router.push({ name: item.routeName })
                            "
                            >{{ item.name }}</a
                        >
                    </div>
                </div>
                <div class="flex items-center">
                    <div class="flex-shrink-0">
                        <button
                            type="button"
                            class="relative inline-flex items-center px-4 py-2 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-500 hover:bg-indigo-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-indigo-500"
                        >
                            <PlusSmIcon
                                class="-ml-1 mr-2 h-5 w-5"
                                aria-hidden="true"
                            />
                            <span>New Job</span>
                        </button>
                    </div>
                    <div
                        class="hidden md:ml-4 md:flex-shrink-0 md:flex md:items-center"
                    >
                        <button
                            type="button"
                            class="bg-gray-800 p-1 rounded-full text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white"
                        >
                            <span class="sr-only">View notifications</span>
                            <BellIcon class="h-6 w-6" aria-hidden="true" />
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <DisclosurePanel class="md:hidden">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <DisclosureButton
                    v-for="item in navigation"
                    :key="item.name"
                    as="a"
                    :href="item.href"
                    :class="[
                        item.current
                            ? 'bg-gray-900 text-white'
                            : 'text-gray-300 hover:bg-gray-700 hover:text-white',
                        'block px-3 py-2 rounded-md text-base font-medium',
                    ]"
                    :aria-current="item.current ? 'page' : undefined"
                    >{{ $t(item.name) }}</DisclosureButton
                >
            </div>
            <div class="pt-4 pb-3 border-t border-gray-700">
                <div class="flex items-center px-5 sm:px-6">
                    <div class="flex-shrink-0">
                        <img
                            class="h-10 w-10 rounded-full"
                            :src="user.imageUrl"
                            alt=""
                        />
                    </div>
                    <div class="ml-3">
                        <div class="text-base font-medium text-white">
                            {{ user.name }}
                        </div>
                        <div class="text-sm font-medium text-gray-400">
                            {{ user.email }}
                        </div>
                    </div>
                    <button
                        type="button"
                        class="ml-auto flex-shrink-0 bg-gray-800 p-1 rounded-full text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white"
                    >
                        <span class="sr-only">View notifications</span>
                        <BellIcon class="h-6 w-6" aria-hidden="true" />
                    </button>
                </div>
                <div class="mt-3 px-2 space-y-1 sm:px-3">
                    <DisclosureButton
                        v-for="item in userNavigation"
                        :key="item.name"
                        as="a"
                        :href="item.href"
                        class="block px-3 py-2 rounded-md text-base font-medium text-gray-400 hover:text-white hover:bg-gray-700"
                        >{{ $t(item.name) }}</DisclosureButton
                    >
                </div>
            </div>
        </DisclosurePanel>
    </Disclosure>
</template>

<script>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue';
import { BellIcon, MenuIcon, XIcon } from '@heroicons/vue/outline';
import { PlusSmIcon } from '@heroicons/vue/solid';

const navigation = [
    { name: 'navbar.home', routeName: 'Home', current: true },
    { name: 'Services', routeName: 'Services', current: false },
    { name: 'A propos', routeName: 'about', current: false },
    { name: 'Contact', routeName: 'contact', current: false },
];

export default {
    name: 'Navbar',
    components: {
        Disclosure,
        DisclosureButton,
        DisclosurePanel,
        BellIcon,
        MenuIcon,
        PlusSmIcon,
        XIcon,
    },
    setup() {
        return {
            navigation,
        };
    },
};
</script>
