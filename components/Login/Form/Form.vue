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
        password: z.string().min(2).max(50),
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
            <LoginFormField
                place-holder="username"
                :dark-mode="props.darkMode"
            ></LoginFormField>
            <LoginFormField
                place-holder="password"
                :dark-mode="props.darkMode"
            ></LoginFormField>
            <Button type="submit" :class="darkModeColor"> Submit </Button>
        </div>
    </form>
</template>
