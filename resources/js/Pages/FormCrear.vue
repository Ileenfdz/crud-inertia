<template>
    
     <app-layout>
        <template #header>
            <h2 class="text-xl font-semibold leading-tight text-gray-800">Crear Producto</h2>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="overflow-hidden bg-white shadow-xl sm:rounded-lg">
                    
                <form @submit.prevent="submit" class="mb-6">
                <div class="grid grid-cols-1 gap-5 mt-5 md:grid-cols-2 md:gap-8 mx-7">
                
                <div class="grid grid-cols-1">
                    <label class="text-xs font-semibold text-gray-500 uppercase md:text-sm text-light">Descripción</label>
                    <input 
                    id="descripcion"
                    v-model="form.descripcion"
                    class="px-3 py-2 mt-1 border-2 border-purple-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="Descripción" 
                    />
                </div>
                
                <div class="grid grid-cols-1">
                    <label class="text-xs font-semibold text-gray-500 uppercase md:text-sm text-light">Precio</label>
                    <input         
                        id="precio"
                        v-model="form.precio"                
                    class="px-3 py-2 mt-1 border-2 border-purple-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="Precio" 
                    />
                </div>
                </div>
            
            
                <div class='flex justify-end gap-4 pt-5 pb-5 pr-5 md:gap-8'>      
                <Link
                    :href="route('productos.index')"                    
                    class='w-auto px-4 py-2 font-medium text-white bg-gray-500 rounded-lg shadow-xl hover:bg-gray-700' type="button">
                    Cancelar
                </Link> 
                <button 
                    type="submit"
                    class='w-auto px-4 py-2 font-medium text-white bg-purple-500 rounded-lg shadow-xl hover:bg-purple-700'
                >
                    Guardar
                </button>
                </div>
            
                </form>
										
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import { Head, Link } from '@inertiajs/inertia-vue3';
export default {
    components:{
        AppLayout,
        Head,
        Link,
    },
    props:{
        errors: Object
    },
    data(){
        return{
            form:{
                descripcion:null,
                precio:null
            }
        }
    },
    methods:{
        submit(){
            this.$inertia.post(route('productos.store'), this.form);
        }
    }
}
</script>