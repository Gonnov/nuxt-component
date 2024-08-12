<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import { useVModel } from "@vueuse/core";
import { cn } from "@/lib/utils";
import { ref } from "vue";

const props = defineProps<{
    defaultValue?: string | number;
    modelValue?: string | number;
    class?: HTMLAttributes["class"];
    darkMode?: boolean;
}>();

const emits = defineEmits<{
    (e: "update:modelValue", payload: string | number): void;
}>();

const modelValue = useVModel(props, "modelValue", emits, {
    passive: true,
    defaultValue: props.defaultValue,
});

const showPassword = ref(false);
</script>

<template>
    <div class="relative">
        <input
            v-model="modelValue"
            :class="
                cn(
                    'flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50  pr-10',
                    props.class
                )
            "
            :type="showPassword ? 'text' : 'password'"
            placeholder="password"
        />
        <div v-if="showPassword === false">
            <Icon
                name="material-symbols-light:visibility-off-outline"
                class="absolute right-3 top-1/2 transform -translate-y-1/2"
                @click="showPassword = true"
            />
        </div>
        <div v-else>
            <Icon
                name="material-symbols-light:visibility-outline"
                class="absolute right-3 top-1/2 transform -translate-y-1/2"
                @click="showPassword = false"
            />
        </div>
    </div>
</template>
