<script setup>
import { useDark, useToggle } from "@vueuse/core";
import { Search, Heart, ShoppingCart, User, Sun, Moon } from "lucide-vue-next";
import Logo from "@/Components/Logo.vue";

import {
    DropdownMenu,
    DropdownMenuContent,
    DropdownMenuItem,
    DropdownMenuLabel,
    DropdownMenuSeparator,
    DropdownMenuTrigger,
} from '@/Components/ui/dropdown-menu'

import {
    Sheet,
    SheetContent,
    SheetDescription,
    SheetHeader,
    SheetTitle,
    SheetTrigger,
} from '@/Components/ui/sheet'

const isDark = useDark()
const toggleDark = useToggle(isDark)
</script>

<template>
    <nav>
        <div class="flex items-center justify-between max-w-screen-xl py-2 mx-auto">
            <!-- Logo -->
            <Link :href="route('home')">
            <div class="flex items-center gap-2">
                <Logo class="w-8" />
                <span class="text-2xl font-semibold">MyStore</span>
            </div>
            </Link>

            <!-- Options -->
            <div>
                <ul class="flex items-center gap-1">
                    <li>
                        <Link
                            class="grid w-10 h-10 rounded-lg place-items-center hover:bg-secondary hover:text-secondary-foreground">
                        <Search class="w-5 h-5" />
                        </Link>
                    </li>
                    <li>
                        <Link
                            class="grid w-10 h-10 rounded-lg place-items-center hover:bg-secondary hover:text-secondary-foreground">
                        <Heart class="w-5 h-5" />
                        </Link>
                    </li>
                    <li>
                        <Sheet>
                            <SheetTrigger class="grid w-10 h-10 rounded-lg place-items-center hover:bg-secondary hover:text-secondary-foreground">
                                <ShoppingCart class="w-5 h-5" />
                            </SheetTrigger>
                            <SheetContent>
                                <SheetHeader>
                                    <SheetTitle>Are you sure absolutely sure?</SheetTitle>
                                    <SheetDescription>
                                        This action cannot be undone. This will permanently delete your account
                                        and remove your data from our servers.
                                    </SheetDescription>
                                </SheetHeader>
                            </SheetContent>
                        </Sheet>
                    </li>
                    <li>
                        <DropdownMenu>
                            <DropdownMenuTrigger
                                class="grid w-10 h-10 rounded-lg place-items-center hover:bg-secondary hover:text-secondary-foreground">
                                <User class="w-5 h-5" />
                            </DropdownMenuTrigger>
                            <DropdownMenuContent>
                                <DropdownMenuItem>
                                    <Link class="w-full">Login</Link>
                                </DropdownMenuItem>
                            </DropdownMenuContent>
                        </DropdownMenu>
                    </li>
                    <li>
                        <button @click="toggleDark()"
                            class="grid w-10 h-10 rounded-lg place-items-center hover:bg-secondary hover:text-secondary-foreground">
                            <Sun v-if="isDark" class="w-5 h-5" />
                            <Moon v-if="!isDark" class="w-5 h-5" />
                        </button>
                    </li>
                </ul>
            </div>
        </div>
        <div class="bg-secondary">
            <div class="max-w-screen-xl py-1 mx-auto">
                <ul class="flex gap-6">
                    <li class="font-semibold">
                        <Link>Men's</Link>
                    </li>
                    <li class="font-semibold">
                        <Link>Women's</Link>
                    </li>
                    <li class="font-semibold">
                        <Link>Kid's</Link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>