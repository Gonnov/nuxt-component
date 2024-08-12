<script setup lang="ts">
import { vAutoAnimate } from "@formkit/auto-animate/vue";
// import InputPassword from "~/components/ui/input/InputPassword.vue";
let props = defineProps({
    placeHolder: {
        type: String,
        default: "",
    },
    darkMode: Boolean,
});
let darkModeColor = props.darkMode
    ? "bg-stone-600 border-stone-500"
    : "bg-white";
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
                    <InputPassword
                        v-bind="componentField"
                        :class="darkModeColor"
                        placeholder="password"
                    />
                </div>
                <div v-else>
                    <Input
                        v-bind="componentField"
                        :class="darkModeColor"
                        place-holder="email"
                    />
                </div>
            </FormControl>
            <FormMessage />
        </FormItem>
    </FormField>
</template>
