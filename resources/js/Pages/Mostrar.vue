<template>
    <app-layout>
        <template #header>
            <h1 class="py-4 text-2xl font-bold leading-7 text-center text-gray-300 sm:text-3xl sm:truncate bg-gradient-to-l from-indigo-500 to-indigo-800 ">MOSTRAR LOS PRODUCTOS</h1>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="overflow-hidden bg-white shadow-xl sm:rounded-lg">

                 <Link
                  :href="route('productos.create')"
                  class="flex-shrink-0 px-4 py-2 text-base font-semibold text-white bg-blue-500 rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-blue-200" type="button">
                     Nuevo
                 </Link>

                    <table class="min-w-full mx-auto mt-5 text-gray-100 bg-gray-800 rounded-t-lg">
                        <thead>
                        <tr class="text-left border-b border-gray-300">
                            <th scope="col" class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-100 uppercase">Descripción</th>
                            <th scope="col" class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-100 uppercase">Precio</th>
                            <th scope="col" class="px-6 py-3 text-xs font-medium tracking-wider text-center text-gray-100 uppercase">Acciones</th>
                        </tr>
                        </thead>
                        <tbody class="text-gray-200 bg-gray-700 border-b border-gray-600">
                        <tr v-for="producto in productos" :key="producto.id">
                            <td class="px-6 py-4 whitespace-nowrap">
                                <div class="flex items-center">
                                <div class="ml-4">
                                <div class="text-sm font-medium">{{ producto.descripcion }}</div>
                                </div>
                                </div>
                            </td>
                            <td class="px-6 py-4 whitespace-nowrap">
                                <div class="text-sm"><span>$ </span>{{ producto.precio }}</div>                    
                            </td>
                            <td class="flex m-2">
                            <Link 
                                :href="route('productos.edit', producto.id)"
                                class="flex-shrink-0 px-4 py-2 text-base font-semibold text-white bg-purple-600 rounded-lg shadow-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2 focus:ring-offset-purple-200" type="button">
                                Editar
                            </Link>
                            <Link
                                as="button" 
                                type="button"
                                method="delete"
                                :href="route('productos.destroy', producto.id)"
                                class="flex-shrink-0 px-4 py-2 text-base font-semibold text-white bg-pink-500 rounded-lg shadow-md hover:bg-pink-700 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:ring-offset-2 focus:ring-offset-pink-200" >
                                Borrar
                            </Link>
                            </td>
                        </tr>   
                        </tbody>
                    </table>

                </div>    
            </div>
       </div>    


    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import { Head, Link } from '@inertiajs/inertia-vue3';
export default {
    props:{
        productos: Array
    },
    components:{
        AppLayout,
        Head,
        Link,
    }
};
</script>