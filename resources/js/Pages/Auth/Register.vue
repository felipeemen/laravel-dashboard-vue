<script lang="ts">
export const description = "A sign up form with first name, last name, email and password inside a card. There's an option to sign up with GitHub and a link to login if you already have an account"
export const iframeHeight = "600px"
export const containerClass = "w-full h-screen flex items-center justify-center px-4"
</script>

<script setup lang="ts">
import { Button } from "../../components/ui/button"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "../../components/ui/card"
import { Input } from "../../components/ui/input"
import { Label } from "../../components/ui/label"

import { ref } from "vue"
import { useForm } from "@inertiajs/vue3"

const form = useForm({
    name: "",
    email: "",
    password: "",
});
const errors = ref([]);

const submit = () => {
    form.post("/auth/register", {
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
                <CardTitle class="text-xl">
                    Sign Up
                </CardTitle>
                <CardDescription>
                    Enter your information to create an account
                </CardDescription>
            </CardHeader>
            <CardContent>
                <form @submit.prevent="submit">
                    <div class="grid gap-4">
                        <div class="grid gap-4">
                            <div class="grid gap-2">
                                <Label for="name">Nome</Label>
                                <Input id="name" placeholder="" v-model="form.name" :class="{ 'is-invalid': errors.name }" required />
                                <span v-if="errors.name">{{ errors.name }}</span>
                            </div>
                        </div>
                        <div class="grid gap-2">
                            <Label for="email">E-mail</Label>
                            <Input
                                id="email"
                                type="email"
                                v-model="form.email"
                                :class="{ 'is-invalid': errors.email }"
                                placeholder=""
                                required
                            />
                            <span v-if="errors.email">{{ errors.email }}</span>
                        </div>
                        <div class="grid gap-2">
                            <Label for="password">Senha</Label>
                            <Input id="password" v-model="form.password" :class="{ 'is-invalid': errors.password }" type="password" />
                            <span v-if="errors.password">{{ errors.password }}</span>
                        </div>
                        <Button type="submit" class="w-full">
                            Criar Conta
                        </Button>
                    </div>
                    <div class="mt-4 text-center text-sm">
                        Already have an account?
                        <a href="#" class="underline">
                            Sign in
                        </a>
                    </div>
                </form>
            </CardContent>
        </Card>
    </div>
</template>
