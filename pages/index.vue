
<template>
    <div>
        <v-row class="my-5">
        <v-col cols="12">
           
        </v-col>    
        </v-row>
        <v-row>
            <v-col cols="12">
                <v-row v-show="grid">
                    <v-col v-for="(product,i) in products"
                     :key="i" 
                     cols="12"
                      lg="4" 
                      sm="6"
                      >
                    <v-card class="mx-auto pb-2">
                        <v-img :src="product.image" height="200px" cover
                        @click="grid = !grid" >
                        <template v-slot:placeholder>
                            
                            <v-row align-content="center" class="fill-height ma-0" justify="center">
                                <v-progress-circular color="grey lighten-5"
                                indeterminate>

                                </v-progress-circular>
                             </v-row>
                            </template>    
                        </v-img>
                        <v-card-title class="text-capitalize">
                           {{product.name}} 
                        </v-card-title>
                        <v-card-subtitle> ${{product.price}}
                          
                        </v-card-subtitle>
                        
                        <v-card-actions>
                            <v-btn color="primary">Read More 
                            
                            </v-btn>
                            <!-- <v-btn class="bg-primary" @click="cartStore.add(product.id)">
                                Add to Cart </v-btn> -->
                                <!-- <v-btn class="bg-primary">Add to Cart </v-btn> -->
                        </v-card-actions>
                    </v-card>    
                    </v-col>

                </v-row>
            <v-row v-show="!grid" v-for="(product) in products" :key="product.id" 
            :product="product">
               
               
                <v-col cols="4">
                    <v-img :src="product.image" height="200px" cover>
                        <template v-slot:placeholder>
                            <v-row align-content="center" class="fill-height ma-0" justify-content="center">
                                <v-progress-circular color="grey lighten-5"
                                indeterminate>
                                    
                                </v-progress-circular>

                            </v-row>

                        </template>

                    </v-img>
                    </v-col>
                    <v-col cols="12" md="8">
                        <v-card-title class="text-capitalize">
                            {{product.name}} </v-card-title>
                              
                            <v-card-subtitle >
                            ${{product.price}} </v-card-subtitle>
                         
                            <v-card-text>
                            {{product.description}} </v-card-text>
           
                            <v-card-actions>
                                <v-btn color="primary">Read More</v-btn>
                           <v-btn class="ml-2 bg-primary" @click="cartStore.add(product.id)">
                            Add to Cart

                           </v-btn>
                            </v-card-actions>



                    </v-col>

            </v-row>
            </v-col>
        </v-row>
        </div>
</template>
<script setup>

import data from "../data";
import { useCartStore }from '../stores/cart'
const cartStore = useCartStore();
const grid=ref(true);
const products = ref(data);


</script>