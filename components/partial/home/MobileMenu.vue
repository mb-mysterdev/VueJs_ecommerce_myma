<template>
    <div class="mobile-menu-container">
        <div class="mobile-menu-wrapper">
            <span class="mobile-menu-close" @click="hideMobileMenu">
                <i class="icon-close"></i>
            </span>
            <form action="#" method="get" class="mobile-search" @submit.prevent="submitSearchForm">
                <label for="mobile-search" class="sr-only">Search</label>
                <input
                    type="search"
                    class="form-control"
                    name="mobile-search"
                    id="mobile-search"
                    v-model="searchTerm"
                    placeholder="Search product ..."
                    required
                />
                <button class="btn btn-primary" type="submit">
                    <i class="icon-search"></i>
                </button>
            </form>
            <nav class="mobile-nav">
                <ul class="mobile-menu">
                    <li>
                        <nuxt-link to="/">Home</nuxt-link>
                    </li>
                    <li>
                        <nuxt-link to="/shop/sidebar/list">Shop</nuxt-link>
                        <ul>
                            <li>
                                <nuxt-link to="/shop/sidebar/list">Shop List</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/sidebar/2cols">Shop Grid 2 Columns</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/sidebar/3cols">Shop Grid 3 Columns</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/sidebar/4cols">Shop Grid 4 Columns</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/nosidebar/boxed">
                                    <span>
                                        Shop Boxed No Sidebar
                                        <span class="tip tip-hot">Hot</span>
                                    </span>
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/nosidebar/fullwidth">Shop Fullwidth No Sidebar</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/category/boxed">Product Category Boxed</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/category/fullwidth">
                                    <span>
                                        Product Category Fullwidth
                                        <span class="tip tip-new">New</span>
                                    </span>
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/cart">Cart</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/checkout">Checkout</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/wishlist">Wishlist</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/shop/dashboard">My Account</nuxt-link>
                            </li>
                        </ul>
                    </li>
                    <li>
                        <nuxt-link
                            to="/product/default/dark-yellow-lace-cut-out-swing-dress"
                            class="sf-with-ul"
                        >Product</nuxt-link>
                        <ul>
                            <li>
                                <nuxt-link
                                    to="/product/default/dark-yellow-lace-cut-out-swing-dress"
                                >Default</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/product/centered/beige-ring-handle-circle-cross-body-bag"
                                >Centered</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/product/extended/yellow-tie-strap-block-heel-sandals"
                                >
                                    <span>
                                        Extended Info
                                        <span class="tip tip-new">New</span>
                                    </span>
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/product/gallery/beige-metal-hoop-tote-bag">Gallery</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/product/sticky/brown-faux-fur-longline-coat"
                                >Sticky Info</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/product/sidebar/beige-v-neck-button-cardigan"
                                >Boxed With Sidebar</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/product/fullwidth/black-faux-leather-chain-trim-sandals"
                                >Full Width</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/product/masonry/black-denim-dungaree-dress"
                                >Masonry Sticky Info</nuxt-link>
                            </li>
                        </ul>
                    </li>
                    <li>
                        <nuxt-link to="/pages/about">Pages</nuxt-link>
                        <ul>
                            <li>
                                <nuxt-link to="/pages/about" class="sf-with-ul">About</nuxt-link>

                                <ul>
                                    <li>
                                        <nuxt-link to="/pages/about">About 01</nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/pages/about-2">About 02</nuxt-link>
                                    </li>
                                </ul>
                            </li>
                            <li>
                                <nuxt-link to="/pages/contact" class="sf-with-ul">Contact</nuxt-link>

                                <ul>
                                    <li>
                                        <nuxt-link to="/pages/contact">Contact 01</nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/pages/contact-2">Contact 02</nuxt-link>
                                    </li>
                                </ul>
                            </li>
                            <li>
                                <nuxt-link to="/pages/login">Login</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/pages/faq">FAQs</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/pages/404">Error 404</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/pages/coming-soon">Coming Soon</nuxt-link>
                            </li>
                        </ul>
                    </li>
                    <li>
                        <nuxt-link to="/blog/classic" class="sf-with-ul">Blog</nuxt-link>
                        <ul>
                            <li>
                                <nuxt-link to="/blog/classic">Classic</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/blog/listing">Listing</nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/blog/grid/grid-2">Grid</nuxt-link>
                                <ul>
                                    <li>
                                        <nuxt-link to="/blog/grid/grid-2">Grid 2 columns</nuxt-link>
                                    </li>
                                </ul>
                            </li>
                            <li>
                                <nuxt-link to="/blog/masonry/masonry-2">Masonry</nuxt-link>
                                <ul>
                                    <li>
                                        <nuxt-link to="/blog/masonry/masonry-3">Masonry 3 columns</nuxt-link>
                                    </li>
                                </ul>
                            </li>
                            <li>
                                <nuxt-link to="/blog/mask/grid">Mask</nuxt-link>
                                <ul>
                                    <li>
                                        <nuxt-link to="/blog/mask/grid">Blog mask grid</nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/blog/mask/masonry">Blog mask masonry</nuxt-link>
                                    </li>
                                </ul>
                            </li>
                            <li>
                                <nuxt-link
                                    to="/blog/single/default/cras-ornare-tristique-elit."
                                >Single Post</nuxt-link>
                                <ul>
                                    <li>
                                        <nuxt-link
                                            to="/blog/single/default/cras-ornare-tristique-elit."
                                        >Default with sidebar</nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link
                                            to="/blog/single/fullwidth/fusce-pellentesque-suscipit."
                                        >Fullwidth no sidebar</nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link
                                            to="/blog/single/sidebar/utaliquam-sollicitzdvudin-leo."
                                        >Fullwidth with sidebar</nuxt-link>
                                    </li>
                                </ul>
                            </li>
                        </ul>
                    </li>
                </ul>
            </nav>
            <div class="social-icons">
                <a class="social-icon" target="_blank" title="Facebook" href="#">
                    <i class="icon-facebook-f"></i>
                </a>
                <a class="social-icon" target="_blank" title="Twitter" href="#">
                    <i class="icon-twitter"></i>
                </a>
                <a class="social-icon" target="_blank" title="Instagram" href="#">
                    <i class="icon-instagram"></i>
                </a>
                <a class="social-icon" target="_blank" title="Youtube" href="#">
                    <i class="icon-youtube"></i>
                </a>
            </div>
        </div>
    </div>
</template>
<script>
import Tabs from '~/components/elements/Tabs';
import { mobileMenu } from '~/utilities/common.js';

export default {
    data: function() {
        return {
            searchTerm: ''
        };
    },
    mounted: function() {
        mobileMenu();
    },
    methods: {
        hideMobileMenu: function() {
            document.querySelector('body').classList.remove('mmenu-active');
        },
        submitSearchForm: function() {
            this.hideMobileMenu();
            this.$router.push({
                path: '/shop/sidebar/3cols',
                query: {
                    searchTerm: this.searchTerm
                }
            });
        }
    }
};
</script>
