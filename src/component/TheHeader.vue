<template>
    <header class="header">
        <nav class="navbar has-background-black is-dark" :class="{ 'has-shadow': hasOffset }">
            <div class="navbar-brand">
                <div class="navbar-item">
                    <img src="/src/assets/logo.png">
                </div>
            </div>
            <div class="container">
                <div class="navbar-menu">
                    <div class="navbar-start">
                        <a
                            v-for="item in setcions"
                            :key="item.path"
                            :href="item.path"
                            class="navbar-item"
                        >
                            {{ item.title }}
                        </a>
                    </div>

                    <div class="navbar-end">
                        <div class="navbar-item">
                            <button
                                type="button"
                                class="button is-link is-small is-rounded"
                                @click.stop="buy">
                                Buy
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    props: {
        hasOffset: {
            type: Boolean,
            default: false,
        }
    },
    data: () => ({
        hasShadow: false,
        setcions: [
            {
                title: 'Store',
                path: '/#store',
            },
            {
                title: 'Discount',
                path: '/#discount',
            },
            {
                title: 'About',
                path: '/#about',
            }
        ],
    }),
    methods: {
        buy() {
            alert('Mock');
        },
    },
};
</script>

<style lang="scss" scoped>
.header {
    width: 100%;
    position: sticky;
    top: 0;
}
</style>