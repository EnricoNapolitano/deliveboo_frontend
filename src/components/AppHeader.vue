<script>
import { store } from '../data/store';
export default {
    name: 'AppHeader',
    data() {
        return {
            store,
            //counter: [],
        }
    },
    methods: {

        counting_order() {

            let dishSum = 0;
            let storageDishSum = 0;
            store.cart.forEach(dish => {
                dishSum += dish.amount
            })

            if (!localStorage.getItem('orders')) {
                return dishSum
            } else if (localStorage.getItem('orders')) {
                const storage = JSON.parse(localStorage.getItem('orders'));
                storage.forEach(storageDish => {
                    storageDishSum += storageDish.amount
                });
                return store.cart.length ? dishSum : storageDishSum;
            }
        }
    }
}
</script>

<template>
    <nav class="navbar navbar-expand-md bg-custom-secondary header-style">
        <div class="container">
            <div class="w-100 d-flex justify-content-between">
                <div class="collapse navbar-collapse d-flex justify-content-between align-items-center p-0"
                    id="navbarSupportedContent">

                    <!-- Left Side Of Navbar -->
                    <div class="navMenu d-flex align-items-center">
                        <router-link :to="{ name: 'home' }" class="text-decoration-none text-dark">
                            <div class=" logo d-flex align-items-center">
                                <img src="http://localhost:5174/img/logo-400x400.png" alt="logo deliveboo"
                                    class="d-flex align-items-center">
                                <h2 class="m-0 ms-2 p-0 fw-bold d-md-block">DeliveBoo</h2>
                            </div>
                        </router-link>
                    </div>

                    <!-- right Side Of Navbar -->
                    <div class="dropdown d-lg-none d-block mt-3 ms-2">
                        <button class=" border-0 bg-transparent text-white" type="button" data-bs-toggle="dropdown">
                            <i class="fa-regular fa-user fs-2 " style="color: #fff;"></i>
                        </button>

                        <!-- dropdown menu -->
                        <ul class="dropdown-menu">
                            <li> <a href="http://127.0.0.1:8000/login" class="me-3  dropdown-item text-dark">Accedi</a></li>
                            <li><a href="http://127.0.0.1:8000/register" class=" dropdown-item text-dark">Crea un
                                    Account</a></li>
                            <li>
                                <router-link :to="{ name: 'CartPage' }" class=" dropdown-item text-dark">
                                    <i class="fa-solid fa-cart-shopping"></i> Carrello
                                </router-link>
                            </li>
                        </ul>
                    </div>

                    <!-- horizontal menu -->
                    <div class="d-none d-lg-flex justify-content-center align-items-center translate-down mt-3 ms-4">
                        <a href="http://127.0.0.1:8000/login" class="me-3 ">Accedi</a>
                        <a href="http://127.0.0.1:8000/register" class="me-3 ">Crea un Account</a>
                        <div class="p-relative">
                            <router-link :to="{ name: 'CartPage' }">
                                <i class="fa-solid fa-cart-shopping"></i>
                                <div v-if="counting_order() !== 0" class="counter">
                                    {{ counting_order() }}
                                </div>
                            </router-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
h2 {
    color: white
}

.header-style {
    min-height: 120px;
    box-shadow: 0 2px 5px 1px rgba(0, 0, 0, 0.1);

    position: sticky;
    top: 0;
    left: 0;
    right: 0;
    z-index: 6;

    a {
        color: var(--white);
        text-decoration: none;

        font-size: 20px;

        transition: 0.5s ease;

        img {
            width: 80px;
        }

        h2 {
            font-weight: 700;
            font-size: 60px;
        }

        // &:active {
        //     font-size: 5rem;
        // }
    }
}

i {
    font-size: 20px;
}

.dropdown-menu {
    transform: translateX(-80%);
}

.p-relative {
    position: relative;
}

.counter {
    font-size: 14px;
    padding: 2px 9px;
    border-radius: 50%;
    color: black;
    background-color: #fec927;
    box-shadow: 0px 0px 2px #00000038;

    position: absolute;
    bottom: 12px;
    left: 8px;
}

a:hover {
    font-size: 25px;
    font-weight: bolder;

    transition: 0.5s ease;
}
</style>
