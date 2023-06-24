<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import DangerButton from '@/Components/DangerButton.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
import Swal from 'sweetalert2';
// import DangerButton from 'vendor/laravel/breeze/stubs/inertia-react/resources/js/Components/DangerButton';

const props = defineProps({
    departments: {type:Object}
});

const form = useForm({
    id:''
});

const deleteDepartment = (id, name) => {
    const alerta = Swal.mixin({
        buttonsStyling:true
    });
    alerta.fire({
        title:'Está seguro de eliminar '+name+'?',
        icon:'question', showCancelButton:true,
        confirmButtonText:'<i class="fa-solid fa-check"></i> Si, eliminar',
        confirmButtonText:'<i class="fa-solid fa-ban"></i> Cancelar'
        }).then((result) =>{
            if(result.isConfirmed){
                form.delete(route('departments.destroy', id));
            }
        })
}
</script>


<template>
    <Head title="Departments" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Departments</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>