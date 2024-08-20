<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
let props = defineProps({
    darkMode: Boolean,
});
</script>

<template>
    <Card
        class="w-[350px]"
        :class="props.darkMode ? 'bg-stone-800' : 'bg-white'"
    >
        <CardHeader>
            <ClientOnly>
                <CardTitle>
                    <h1
                        :class="
                            props.darkMode ? 'text-white' : 'text-stone-900'
                        "
                    >
                        Register
                    </h1>
                </CardTitle>
            </ClientOnly>
        </CardHeader>
        <CardContent>
            <ClientOnly>
                <RegisterForm :dark-mode="props.darkMode" />
            </ClientOnly>
        </CardContent>
    </Card>
</template>
