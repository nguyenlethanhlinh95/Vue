<template>
    <div class="container">
        <h1>Test Component</h1>
        <p>{{ title | toUpperCase }}</p>
        <div class="">
            <input type="text" v-model="filterText">
            <ul>
                <li v-for="item in filteredFruits" :key="item">{{ item }}</li>
            </ul>
        </div>
        <div class="">
        </div>
        <div class="row mb-2">
            <div class="col-lg-12">
                <h1 class="text-title">Animation</h1>
                <div class="">
                    <button class="btn btn-primary" @click="showForm">Show Alert</button>
                </div>
                <br>
                <div class="animated fadeInUp" v-if="show">
                    <transition name="fade">
                        <div class="alert alert-info">This is show info</div>
                    </transition>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                title: 'Hello world',
                filterText: '',
                fruits: ['Apple', 'Banana', 'Mango', 'Melon'],
                show: false
            }
        },
        filters: {
            toUpperCase: function(value) {
                return value.toUpperCase();
            }
        },
        computed: {
            filteredFruits() {
                return this.fruits.filter((element) => {
                    return element.match(this.filterText);
                });
            }
        },
        methods: {
            showForm() {
                let isShow = this.show;
                this.show = !isShow;
            }
        },
    }
</script>

<style>
    .fade-enter {
        opacity: 0;
    }

    .fade-enter-active {
        transition: opacity 1s;
        opacity: 1;
    }

    .fade-leave {

    }

    .fade-leave-active {
        transition: opacity 1s;
        opacity: 0;
    }
</style>