<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives Exercise</h1>
                <!-- Exercise -->
                <!-- Build a Custom Directive which works like v-on (Listen for Events) -->

                <button v-myOn:click="myFunction">Click</button>
                <h1>{{counter}}</h1>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
       directives:{
            'myOn':{
                bind(el, binding, vnode){
                    if(binding.arg=='click'){
                        let func=binding.value;
                        el.addEventListener("click", func );
                    }
                }
            },
        },
        data(){
            return{
                counter:0,
            };
        },
        methods:{
            myFunction(){
                this.counter++;
            }
        }
    }
</script>

<style>
</style>
