<script setup lang="ts">
import { h } from "vue";
import { useForm } from "vee-validate";
import { toTypedSchema } from "@vee-validate/zod";
import * as z from "zod";

import { Button } from "@/components/ui/button";
import { toast } from "@/components/ui/toast";

let props = defineProps({
    darkMode: Boolean,
});

let darkModeColor = props.darkMode
    ? "mt-6 bg-stone-900 w-full"
    : " mt-6 bg-indigo-900 w-full";

const formSchema = toTypedSchema(
    z.object({
        username: z.string().min(2).max(50),
        email: z.string().min(2).max(50),
        password1: z.string().min(2).max(50),
        password2: z.string().min(2).max(50),
    })
);

const { handleSubmit } = useForm({
    validationSchema: formSchema,
});

const onSubmit = handleSubmit((values) => {
    console.log(values);
});
</script>

<template>
    <form
        class="w-full space-y-6 flex justify-center content-center"
        @submit="onSubmit"
    >
        <div>
            <RegisterFormField
                place-holder="username"
                :dark-mode="props.darkMode"
            ></RegisterFormField>
            <RegisterFormField
                place-holder="mail"
                :dark-mode="props.darkMode"
            ></RegisterFormField>
            <RegisterFormField
                place-holder="password"
                :dark-mode="props.darkMode"
            ></RegisterFormField>
            <RegisterFormField
                place-holder="confirm password"
                :dark-mode="props.darkMode"
            ></RegisterFormField>
            <Button type="submit" :class="darkModeColor"> Register </Button>
        </div>
    </form>
</template>
