<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
</script>

<template>
    <Card class="w-[350px]">
        <CardHeader>
            <CardTitle>Login</CardTitle>
        </CardHeader>
        <CardContent>
            <ClientOnly>
                <LoginForm />
            </ClientOnly>
        </CardContent>
    </Card>
</template>
