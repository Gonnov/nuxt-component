<script setup lang="ts">
import { vAutoAnimate } from "@formkit/auto-animate/vue";

let props = defineProps({
    placeHolder: {
        type: String,
        default: "",
    },
    darkMode: Boolean,
});
let darkModeColor = props.darkMode
    ? "bg-stone-600 border-stone-500 text-white"
    : "bg-white";
</script>

<template>
    <FormField v-slot="{ componentField }" :name="placeHolder">
        <FormItem v-auto-animate>
            <FormLabel></FormLabel>
            <FormControl>
                <div v-if="props.placeHolder.includes('password')">
                    <InputPassword
                        v-bind="componentField"
                        :class="darkModeColor"
                        :placeHolder="props.placeHolder"
                    />
                </div>
                <div v-else>
                    <Input
                        v-bind="componentField"
                        :class="darkModeColor"
                        :placeHolder="props.placeHolder"
                    />
                </div>
            </FormControl>
        </FormItem>
    </FormField>
</template>
