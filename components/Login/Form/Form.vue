<script setup lang="ts">
import { h } from "vue";
import { useForm } from "vee-validate";
import { toTypedSchema } from "@vee-validate/zod";
import * as z from "zod";

import { Button } from "@/components/ui/button";
import { toast } from "@/components/ui/toast";

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
        class="w-2/3 space-y-6 flex justify-center content-center"
        @submit="onSubmit"
    >
        <div>
            <LoginFormField place-holder="username"></LoginFormField>
            <LoginFormField place-holder="password"></LoginFormField>
            <Button type="submit" class="mt-6"> Submit </Button>
        </div>
    </form>
</template>
