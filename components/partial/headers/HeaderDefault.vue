<template>
    <header class="header header-7">
        <sticky-header>
            <div class="header-middle sticky-header">
                <div class="container">
                    <div class="header-left">
                        <button class="mobile-menu-toggler" @click="openMobileMenu">
                            <span class="sr-only">Toggle mobile menu</span>
                            <i class="icon-bars"></i>
                        </button>

                        <nuxt-link to="/" class="logo">
                            <img
                                v-lazy="'./images/logo.png'"
                                class="bg-white"
                                alt="Molla Logo"
                                width="82"
                                height="22"
                            />
                        </nuxt-link>
                    </div>

                    <div class="header-right">
                        <main-menu></main-menu>
                        <header-search></header-search>
                        <wishlist-menu></wishlist-menu>
                        <cart-menu></cart-menu>
                    </div>
                </div>
            </div>
        </sticky-header>
    </header>
</template>

<script>
import CartMenu from '~/components/partial/headers/shared/CartMenu';
import WishlistMenu from '~/components/partial/headers/shared/WishlistMenu';
import MainMenu from '~/components/partial/headers/shared/MainMenu';
import HeaderSearch from '~/components/partial/headers/shared/HeaderSearch';
import StickyHeader from '~/components/elements/StickyHeader';

export default {
    components: {
        CartMenu,
        WishlistMenu,
        MainMenu,
        HeaderSearch,
        StickyHeader
    },
    computed: {
        isFullwidth: function() {
            return this.$route.path.includes('fullwidth');
        }
    },
    methods: {
        openSignInModal: function() {
            this.$modal.show(
                () => import('~/components/elements/modals/SignInModal'),
                {},
                { width: '575', height: 'auto', adaptive: true }
            );
        },
        openMobileMenu: function() {
            document.querySelector('body').classList.add('mmenu-active');
        }
    }
};
</script>