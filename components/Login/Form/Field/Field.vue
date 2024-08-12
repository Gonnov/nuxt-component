<script setup lang="ts">
import { vAutoAnimate } from "@formkit/auto-animate/vue";
// import InputPassword from "~/components/ui/input/InputPassword.vue";
let props = defineProps({
    placeHolder: {
        type: String,
        default: "",
    },
});
let type = "text";
if (props.placeHolder === "password") {
    type = "password";
}
</script>

<template>
    <FormField v-slot="{ componentField }" :name="placeHolder">
        <FormItem v-auto-animate>
            <FormLabel></FormLabel>
            <FormControl>
                <div v-if="type === 'password'">
                    <InputPassword v-bind="componentField" />
                </div>
                <div v-else>
                    <Input v-bind="componentField" />
                </div>
            </FormControl>
            <FormMessage />
        </FormItem>
    </FormField>
</template>
