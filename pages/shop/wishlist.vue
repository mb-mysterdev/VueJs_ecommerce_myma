<template>
    <main class="main">
        <page-header title="Wishlist" subtitle="Shop"></page-header>
        <nav class="breadcrumb-nav">
            <div class="container">
                <ol class="breadcrumb">
                    <li class="breadcrumb-item">
                        <nuxt-link to="/">Home</nuxt-link>
                    </li>
                    <li class="breadcrumb-item">
                        <nuxt-link to="/shop/sidebar/list">Shop</nuxt-link>
                    </li>
                    <li class="breadcrumb-item active">Wishlist</li>
                </ol>
            </div>
        </nav>

        <div class="page-content d-flex align-items-center" style="min-height: 53rem">
            <div class="container" v-if="wishlist.length > 0" key="hasWishlist">
                <table class="table table-wishlist table-mobile">
                    <thead>
                        <tr>
                            <th>Product</th>
                            <th>Price</th>
                            <th>Stock Status</th>
                            <th></th>
                            <th></th>
                        </tr>
                    </thead>

                    <tbody>
                        <tr v-for="(product, index) in wishlist" :key="index">
                            <td class="product-col">
                                <div class="product">
                                    <figure class="product-media">
                                        <nuxt-link :to="'/product/default/' + product.slug">
                                            <img
                                                v-lazy="`${baseUrl}${product.sm_pictures[0].url}`"
                                                alt="Product"
                                                :width="product.sm_pictures[0].width"
                                                :height="product.sm_pictures[0].height"
                                            />
                                        </nuxt-link>
                                    </figure>

                                    <h3 class="product-title">
                                        <nuxt-link
                                            :to="'/product/default/' + product.slug"
                                        >{{ product.name }}</nuxt-link>
                                    </h3>
                                </div>
                            </td>
                            <td
                                class="price-col"
                            >${{ product.discount ? product.salePrice : product.price }}</td>
                            <td class="stock-col">
                                <span
                                    :class="product.stock && product.stock == 0 ? 'out-of-stock' : 'in-stock'"
                                >{{ product.stock && product.stock == 0 ? 'Out of stock' : 'In stock' }}</span>
                            </td>
                            <td class="action-col">
                                <div class="dropdown">
                                    <nuxt-link
                                        class="btn btn-block btn-outline-primary-2"
                                        :to="'/product/default/' + product.slug"
                                        v-if="product.variants.length > 0"
                                    >
                                        <i class="icon-list-alt"></i>Select Options
                                    </nuxt-link>
                                    <button
                                        class="btn btn-block btn-outline-primary-2"
                                        @click.prevent="moveToCart({product: product})"
                                        v-else
                                    >
                                        <i class="icon-cart-plus"></i>Add to Cart
                                    </button>
                                </div>
                            </td>
                            <td class="remove-col">
                                <button
                                    class="btn-remove"
                                    @click.prevent="removeFromWishlist({product: product})"
                                >
                                    <i class="icon-close"></i>
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>

                <div class="wishlist-share">
                    <div class="social-icons social-icons-sm mb-2">
                        <label class="social-label">Share on:</label>
                        <a href="#" class="social-icon" title="Facebook" target="_blank">
                            <i class="icon-facebook-f"></i>
                        </a>
                        <a href="#" class="social-icon" title="Twitter" target="_blank">
                            <i class="icon-twitter"></i>
                        </a>
                        <a href="#" class="social-icon" title="Instagram" target="_blank">
                            <i class="icon-instagram"></i>
                        </a>
                        <a href="#" class="social-icon" title="Youtube" target="_blank">
                            <i class="icon-youtube"></i>
                        </a>
                        <a href="#" class="social-icon" title="Pinterest" target="_blank">
                            <i class="icon-pinterest"></i>
                        </a>
                    </div>
                </div>
            </div>

            <div class="container" v-else key="noWishlist">
                <div class="text-center">
                    <i class="icon-heart-o wishlist-empty d-block"></i>
                    <span class="d-block mt-2">No products added to wishlist</span>
                    <nuxt-link to="/shop/sidebar/list" class="btn btn-primary mt-2">Go Shop</nuxt-link>
                </div>
            </div>
        </div>
    </main>
</template>
<script>
import { mapGetters, mapActions } from 'vuex';
import PageHeader from '~/components/elements/PageHeader';
import { baseUrl } from '~/repositories/repository.js';

export default {
    components: {
        PageHeader
    },
    data: function() {
        return {
            baseUrl: baseUrl
        };
    },
    computed: {
        ...mapGetters('wishlist', ['wishlistQty', 'wishlist'])
    },
    methods: {
        ...mapActions('wishlist', ['removeFromWishlist', 'moveToCart'])
    }
};
</script>