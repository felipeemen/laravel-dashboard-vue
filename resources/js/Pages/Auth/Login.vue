<script lang="ts">
export const description = "A simple login form with email and password. The submit button says 'Sign in'."
export const iframeHeight = "600px"
export const containerClass = "w-full h-screen flex items-center justify-center px-4"
</script>

<script setup lang="ts">
import { Button } from "../../components/ui/button"
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from "../../components/ui/card"
import { Input } from "../../components/ui/input"
import { Label } from "../../components/ui/label"
import { ref } from "vue"
import { useForm } from "@inertiajs/vue3"

const form = useForm({
    email: "",
    password: "",
});
const errors = ref([]);

const submit = () => {
    form.post("/auth/login", {
        onError: (error: any) => {
            errors.value = error
        }
    });
}
</script>

<template>
    <div class="mx-auto h-screen flex items-center justify-center">
        <Card class="w-full max-w-sm">
            <CardHeader>
                <CardTitle class="text-2xl">
                    Login
                </CardTitle>
                <CardDescription>
                    Enter your email below to login to your account.
                </CardDescription>
            </CardHeader>
            <CardContent>
                <form @submit.prevent="submit">
                    <div class="grid gap-4">
                        <div class="grid gap-2">
                            <Label for="email">E-mail</Label>
                            <Input id="email" type="email" v-model="form.email" :class="{ 'is-invalid': errors.email }" placeholder="" required />
                            <span v-if="errors.email">{{ errors.email }}</span>
                        </div>
                        <div class="grid gap-2">
                            <Label for="password">Senha</Label>
                            <Input id="password" v-model="form.password" :class="{ 'is-invalid': errors.password }" type="password" required />
                            <span v-if="errors.password">{{ errors.password }}</span>
                        </div>
                        <Button class="w-full" type="submit">
                            Login
                        </Button>
                    </div>
                </form>
            </CardContent>
        </Card>
    </div>
</template>