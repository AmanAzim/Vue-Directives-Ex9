<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives Exercise</h1>
                <!-- Exercise -->
                <!-- Build a Custom Directive which works like v-on (Listen for Events) -->

                <button v-myOn:click="myFunction">Click</button>
                <h1>{{counter}}</h1>
                <hr>
                <button v-myOn2="myFunction2">Click to alert</button>
                <hr>
                <button v-myOn3:click="myFunction">Click</button>
                <h1>{{counter}}</h1>

                <input v-myOn3:input="updateName">
                <p>Name: {{name}}</p>

                <div style="width: 100px; height: 100px; background-color: lightcoral"
                     v-custom:mouseenter=" mouseEnter"
                     v-custom:mouseleave="mouseLeft">
                </div>

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
           'myOn2':{
               bind(el, binding, vnode){
                   el.onclick= binding.value;
               }
           },
           'myOn3':{
               bind(el, binding, vnode){
                   const Event=binding.arg;
                   const fun=binding.value;

                   el.addEventListener(Event, fun);
               }
           },
           'custom':{
               bind(el, binding, vnode){
                   const Event=binding.arg;
                   const fun=binding.value;

                   el.addEventListener(Event, fun);
               }
           },
        },
        data(){
            return{
                counter:0,
                name:'',
            };
        },
        methods:{
            myFunction(){
                this.counter++;
            },
            myFunction2(){
                alert("Aman");
            },
            updateName(event){
              this.name=event.target.value.toLowerCase();
            },
            mouseEnter()
            {
                console.log('Mouse entered');
            },
            mouseLeft()
            {
                console.log('Mouse left');
            }
        }
    }
</script>

<style>
</style>
