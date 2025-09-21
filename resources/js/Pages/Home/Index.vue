<template>
    <div>
        <h1 class="text-3xl text-blue-700">Bem vindo, Felipe</h1>
        <Link href="/dashboard">
            <Button>Clique Aqui</Button>
        </Link>
        
    </div>
</template>

<script setup>
import { Button } from '@/components/ui/button';
import { Link } from '@inertiajs/vue3';
</script>