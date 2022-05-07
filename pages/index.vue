<template>
    <div class="main home-page">
        <div class="intro-slider-container mb-4">
            <div class="swiper-carousel intro-slider swiper-1">
                <div v-swiper:swiper1="carouselSetting1">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide">
                            <div
                                class="intro-slide"
                                v-lazy:background-image="'./images/home/sliders/slide-1.jpg'"
                            >
                                <div class="container intro-content">
                                    <h3 class="intro-subtitle text-primary">SEASONAL PICKS</h3>

                                    <h1 class="intro-title">
                                        Get All
                                        <br />The Good Stuff
                                    </h1>

                                    <nuxt-link
                                        to="/shop/sidebar/4cols"
                                        class="btn btn-outline-primary-2"
                                    >
                                        <span>DISCOVER MORE</span>
                                        <i class="icon-long-arrow-right"></i>
                                    </nuxt-link>
                                </div>
                            </div>
                        </div>
                        <div class="swiper-slide">
                            <div
                                class="intro-slide"
                                v-lazy:background-image="'./images/home/sliders/slide-2.jpg'"
                            >
                                <div class="container intro-content">
                                    <h3 class="intro-subtitle text-primary">all at 50% off</h3>

                                    <h1 class="intro-title text-white">
                                        The Most Beautiful
                                        <br />Novelties In Our Shop
                                    </h1>

                                    <nuxt-link
                                        to="/shop/sidebar/list"
                                        class="btn btn-outline-primary-2 min-width-sm"
                                    >
                                        <span>SHOP NOW</span>
                                        <i class="icon-long-arrow-right"></i>
                                    </nuxt-link>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="swiper-nav">
                    <div class="swiper-prev">
                        <i class="icon-angle-left"></i>
                    </div>
                    <div class="swiper-next">
                        <i class="icon-angle-right"></i>
                    </div>
                </div>
                <div class="swiper-dots swiper-dots-inner"></div>
            </div>
        </div>

        <div
            class="page-content container skeleton-body skel-shop-products"
            :class="{loaded: loaded}"
        >
<!--            <div class="toolbox toolbox-filter">-->
<!--                <div class="toolbox-left">-->
<!--                    <a-->
<!--                        href="#"-->
<!--                        class="filter-toggler"-->
<!--                        :class="{active: toggleState}"-->
<!--                        @click.prevent="toggleState = !toggleState"-->
<!--                    >Filters</a>-->
<!--                    <button class="button filter-toggler mobile-mode" @click="showSidebar">Filters</button>-->
<!--                </div>-->

<!--                <div class="toolbox-right" v-show="!toggleState">-->
<!--                    <ul class="nav-filter product-filter" v-if="! $route.query.category">-->
<!--                        <li class="active">-->
<!--                            <a href="#" @click.prevent="isotopeFilter('iso', 'all', $event)">All</a>-->
<!--                        </li>-->
<!--                        <li>-->
<!--                            <a-->
<!--                                href="#"-->
<!--                                @click.prevent="isotopeFilter('iso', 'furniture', $event)"-->
<!--                            >Furniture</a>-->
<!--                        </li>-->
<!--                        <li>-->
<!--                            <a-->
<!--                                href="#"-->
<!--                                @click.prevent="isotopeFilter('iso', 'lighting', $event)"-->
<!--                            >Lighting</a>-->
<!--                        </li>-->
<!--                        <li>-->
<!--                            <a-->
<!--                                href="#"-->
<!--                                @click.prevent="isotopeFilter('iso', 'decoration', $event)"-->
<!--                            >Decoration</a>-->
<!--                        </li>-->
<!--                        <li>-->
<!--                            <a-->
<!--                                href="#"-->
<!--                                @click.prevent="isotopeFilter('iso', 'electronics', $event)"-->
<!--                            >Electronics</a>-->
<!--                        </li>-->
<!--                    </ul>-->
<!--                    <ul class="nav-filter product-filter" v-else>-->
<!--                        <li>-->
<!--                            <nuxt-link to="/" :class="{active: categorySelected(null)}">All</nuxt-link>-->
<!--                        </li>-->
<!--                    </ul>-->
<!--                </div>-->
<!--            </div>-->

            <button class="sidebar-fixed-toggler" @click="toggleSidebar">
                <i class="icon-cog"></i>
            </button>
            <div class="sidebar-filter-overlay" @click="hideSidebar"></div>
            <vue-slide-toggle :open="toggleState">
                <div class="widget-filter-area" id="product-filter-area">
                    <div class="clean-close">
                        <a href="#" class="widget-filter-clear" @click.prevent="cleanAll">Clean All</a>
                        <a href="#" class="widget-close" @click.prevent="hideSidebar">
                            <i class="icon-close"></i>
                        </a>
                    </div>
                    <div class="filter-area-wrapper">
                        <div class="row">
                            <div class="col-lg-3">
                                <div class="widget">
                                    <h3 class="widget-title">Category:</h3>

                                    <div class="filter-items filter-items-count">
                                        <div class="filter-item">
                                            <nuxt-link
                                                to="/"
                                                :class="{active: categorySelected(null)}"
                                            >All</nuxt-link>
                                            <span class="item-count">15</span>
                                        </div>
                                        <div
                                            class="filter-item"
                                            v-for="(category, index) in homeData.categories"
                                            :key="index"
                                        >
                                            <nuxt-link
                                                :to="{path: $route.path, query: {category: category.slug}}"
                                                :class="{active: categorySelected(category)}"
                                            >{{ category.name }}</nuxt-link>
                                            <span class="item-count">{{ category.count }}</span>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="col-lg-3">
                                <div class="widget">
                                    <h3 class="widget-title">Sort by:</h3>

                                    <div class="filter-items">
                                        <div class="filter-item">
                                            <div class="custom-control custom-checkbox">
                                                <input
                                                    type="radio"
                                                    class="custom-control-input"
                                                    v-model="orderBy"
                                                    value="default"
                                                    name="orderby"
                                                    @change="getProducts"
                                                    id="sort-1"
                                                />
                                                <label
                                                    class="custom-control-label"
                                                    for="sort-1"
                                                >Default</label>
                                            </div>
                                        </div>

                                        <div class="filter-item">
                                            <div class="custom-control custom-checkbox">
                                                <input
                                                    type="radio"
                                                    class="custom-control-input"
                                                    v-model="orderBy"
                                                    value="featured"
                                                    name="orderby"
                                                    @change="getProducts"
                                                    id="sort-2"
                                                />
                                                <label
                                                    class="custom-control-label"
                                                    for="sort-2"
                                                >Popularity</label>
                                            </div>
                                        </div>

                                        <div class="filter-item">
                                            <div class="custom-control custom-checkbox">
                                                <input
                                                    type="radio"
                                                    class="custom-control-input"
                                                    v-model="orderBy"
                                                    value="rating"
                                                    name="orderby"
                                                    @change="getProducts"
                                                    id="sort-3"
                                                />
                                                <label
                                                    class="custom-control-label"
                                                    for="sort-3"
                                                >Average Rating</label>
                                            </div>
                                        </div>

                                        <div class="filter-item">
                                            <div class="custom-control custom-checkbox">
                                                <input
                                                    type="radio"
                                                    class="custom-control-input"
                                                    id="sort-4"
                                                    v-model="orderBy"
                                                    value="new"
                                                    name="orderby"
                                                    @change="getProducts"
                                                />
                                                <label
                                                    class="custom-control-label"
                                                    for="sort-4"
                                                >Newness</label>
                                            </div>
                                        </div>

                                        <div class="filter-item">
                                            <div class="custom-control custom-checkbox">
                                                <input
                                                    type="radio"
                                                    class="custom-control-input"
                                                    id="sort-5"
                                                    name="orderby"
                                                    v-model="orderBy"
                                                    value="low-to-high"
                                                    @change="getProducts"
                                                />
                                                <label
                                                    class="custom-control-label"
                                                    for="sort-5"
                                                >Price: Low to High</label>
                                            </div>
                                        </div>

                                        <div class="filter-item">
                                            <div class="custom-control custom-checkbox">
                                                <input
                                                    type="radio"
                                                    class="custom-control-input"
                                                    id="sort-6"
                                                    name="orderby"
                                                    v-model="orderBy"
                                                    value="high-to-low"
                                                    @change="getProducts"
                                                />
                                                <label
                                                    class="custom-control-label"
                                                    for="sort-6"
                                                >Price: High to Low</label>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="col-lg-3">
                                <div class="widget">
                                    <h3 class="widget-title">Colour:</h3>

                                    <div class="filter-colors filter-colors-vertical">
                                        <nuxt-link
                                            :to="getColorUrl(item)"
                                            :style="{'background-color': item.color}"
                                            v-for="(item, index) in filterData.colors"
                                            :key="index"
                                            :class="{selected: colorSelected(item)}"
                                        >
                                            <span>{{ item.color_name }}</span>
                                        </nuxt-link>
                                    </div>
                                </div>
                            </div>

                            <div class="col-lg-3">
                                <div class="widget">
                                    <h3 class="widget-title">Price:</h3>

                                    <div class="filter-price">
                                        <div
                                            class="filter-price-text d-flex justify-content-between"
                                        >
                                            <span>
                                                Price Range:
                                                <span
                                                    id="filter-price-range"
                                                >{{ priceRangeText }}</span>
                                            </span>
                                            <nuxt-link :to="priceFilterRoute" class="pr-2">Filter</nuxt-link>
                                        </div>

                                        <vue-nouislider
                                            :config="priceSliderConfig"
                                            :values="priceValues"
                                            id="price-slider"
                                            v-if="loaded"
                                        ></vue-nouislider>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </vue-slide-toggle>
            <!-- End #product-filter-area.widget-filter-area -->

            <div class="products-container" v-if="products.length === 0 && loaded">
                <p class="no-results">No products matching your selection.</p>
            </div>
            <div
                class="products-container overflow-hidden"
                v-else
                v-images-loaded.on="handleIsotope"
            >
                <div class="row" v-if="!loaded">
                    <div
                        class="skel-pro product-item furniture col-6 col-md-4 col-lg-3"
                        v-for="item in [0,1,2,3,4,5,6,7]"
                        :key="item"
                    ></div>
                </div>
                <div class="px-3" v-else>
                    <isotope
                        ref="iso"
                        :list="products"
                        :options="isotopeOptions"
                        @layout="onLayout"
                        class="row"
                    >
                        <div
                            class="product-item col-6 col-md-4 col-lg-3"
                            v-for="(product, index) in products"
                            :key="index"
                        >
                            <product-twelve :product="product"></product-twelve>
                        </div>
                    </isotope>
                </div>
            </div>
        </div>

        <div class="load-more-container text-center mt-0 mb-7">
            <a
                href="#"
                class="btn btn-outline-dark-3 btn-load-more"
                @click.prevent="loadMore"
                v-if="loadMoreLoading || hasMore"
            >
                <span>More products</span>
                <i class="icon-refresh" :class="{'load-more-rotating' : loadMoreLoading}"></i>
            </a>
        </div>
    </div>
</template>
<script>
import { mapGetters } from 'vuex';
import { VueSlideToggle } from 'vue-slide-toggle';
import isotope from 'vueisotope';
import imagesLoaded from 'vue-images-loaded';

import ProductTwelve from '~/components/elements/products/ProductTwelve';
import NewsletterModal from '~/components/elements/modals/NewsletterModal';

import Repository, { baseUrl } from '~/repositories/repository.js';
import { carouselSettingSingle } from '~/utilities/carousel';
import { homeData, shopData } from '~/utilities/data';
import { scrollToPageContent } from '~/utilities/common';

export default {
    components: {
        isotope,
        VueSlideToggle,
        ProductTwelve
    },
    directives: {
        imagesLoaded
    },
    data: function() {
        return {
            loaded: false,
            products: [],
            carouselSetting1: {
                ...carouselSettingSingle,
                pagination: {
                    el: '.intro-slider .swiper-dots',
                    clickable: true
                },
                navigation: {
                    nextEl: '.intro-slider .swiper-next',
                    prevEl: '.intro-slider .swiper-prev'
                }
            },
            isotopeOptions: {
                itemSelector: 'portfolio-item',
                layoutMode: 'fitRows',
                percentPosition: false,
                getFilterData: {
                    decoration: function(elem) {
                        if (elem) {
                            return elem.category.find(
                                cat => cat.slug == 'decoration'
                            );
                        } else return false;
                    },
                    lighting: function(elem) {
                        if (elem) {
                            return elem.category.find(
                                cat => cat.slug == 'lighting'
                            );
                        } else return false;
                    },
                    furniture: function(elem) {
                        if (elem) {
                            return elem.category.find(
                                cat => cat.slug == 'furniture'
                            );
                        } else return false;
                    },
                    electronics: function(elem) {
                        if (elem) {
                            return elem.category.find(
                                cat => cat.slug == 'electronics'
                            );
                        } else return false;
                    },
                    all: function(elem) {
                        return true;
                    }
                }
            },
            toggleState: false,
            priceValues: [0, 1000],
            priceSliderConfig: {
                connect: true,
                step: 50,
                margin: 100,
                range: {
                    min: 0,
                    max: 1000
                }
            },
            orderBy: 'default',
            perPage: 28,
            totalCount: 0,
            loadMoreLoading: false,
            homeData: homeData,
            filterData: shopData
        };
    },
    computed: {
        ...mapGetters('demo', ['newsletterShow']),
        priceRangeText: function() {
            return (
                '$' +
                parseInt(this.priceValues[0]) +
                ' — $' +
                parseInt(this.priceValues[1])
            );
        },
        priceFilterRoute: function() {
            let query = {};
            if (this.$route.query.page) {
                for (let key in this.$route.query) {
                    if (key !== 'page') {
                        query[key] = this.$route.query[key];
                    }
                }
            } else {
                query = { ...this.$route.query };
            }

            return {
                path: this.$route.path,
                query: {
                    ...query,
                    minPrice: this.priceValues[0],
                    maxPrice: this.priceValues[1]
                }
            };
        },
        hasMore: function() {
            return this.perPage < this.totalCount;
        }
    },
    watch: {
        $route: function() {
            this.getProducts(true);
        }
    },
    created: function() {
        if (this.$route.query.minPrice && this.$route.query.maxPrice) {
            this.loaded = false;
            this.priceValues = [
                this.$route.query.minPrice,
                this.$route.query.maxPrice
            ];
        } else {
            this.loaded = false;
        }

        this.getProducts();
    },
    mounted: function() {
        if (this.newsletterShow) {
            setTimeout(() => {
                if (this.$route.path == '/' && this.newsletterShow) {
                    this.$modal.show(
                        NewsletterModal,
                        {},
                        { width: '970', height: 'auto', adaptive: true }
                    );
                }
            }, 8000);
        }
    },
    methods: {
        getProducts: async function(samePage = false, loadMore = false) {
            if (!loadMore) this.loaded = false;
            await Repository.get(`${baseUrl}/shop`, {
                params: {
                    ...this.$route.query,
                    orderBy: this.orderBy,
                    perPage: this.perPage,
                    demo: this.currentDemo
                }
            })
                .then(response => {
                    this.products = this.$route.query.category ? [...response.data.products] : response.data.products.slice(20);
                    this.totalCount = response.data.totalCount;
                    this.$nextTick(() => {
                        this.loaded = true;
                    })

                    if (samePage) scrollToPageContent();
                })
                .catch(error => ({ error: JSON.stringify(error) }));
        },
        categorySelected: function(item) {
            return (
                (item == null && !this.$route.query.category) ||
                (this.$route.query.category &&
                    item &&
                    this.$route.query.category == item.slug)
            );
        },
        colorSelected: function(item) {
            return (
                this.$route.query.color &&
                this.$route.query.color.split(',').includes(item.color_name)
            );
        },

        getColorUrl: function(item) {
            let query = {};

            if (!this.$route.query.color) {
                query = {
                    ...this.$route.query,
                    color: item.color_name
                };
            } else if (
                this.$route.query.color.split(',').includes(item.color_name)
            ) {
                query = {
                    ...this.$route.query,
                    color: this.$route.query.color
                        .split(',')
                        .filter(slug => slug !== item.color_name)
                        .join(',')
                };
            } else {
                query = {
                    ...this.$route.query,
                    color: [
                        ...this.$route.query.color.split(','),
                        item.color_name
                    ].join(',')
                };
            }

            let temp = {};
            if (query.page) {
                for (let key in query) {
                    if (key !== 'page') {
                        temp[key] = query[key];
                    }
                }
            } else {
                temp = { ...query };
            }

            return {
                path: this.$route.path,
                query: temp
            };
        },

        loadMore: function() {
            if (this.perPage < this.totalCount) {
                this.perPage += 4;
                this.loadMoreLoading = true;
                setTimeout(() => {
                    this.getProducts(false, true);
                    this.loadMoreLoading = false;
                }, 400);
            }
        },
        cleanAll: function() {
            this.loaded = false;
            this.priceValues = [0, 1000];
            this.$nextTick(function() {
                this.orderBy = 'default';
                this.loaded = true;
                this.$router.push('/');
            });
        },
        handleIsotope: function() {
            if (this.$refs.iso) {
                this.$refs['iso'].layout('fitRows');
            }
        },
        isotopeFilter: function(iso, filterClass, e) {
            this.$refs[iso].filter(filterClass);
            let prevActive = e.currentTarget.parentElement.parentElement.querySelector(
                '.active'
            );
            if (prevActive) {
                prevActive.classList.remove('active');
            }

            e.currentTarget.parentElement.classList.add('active');
        },

        onLayout: function() {
            if (document.querySelector('.nav-filter li.active')) {
                document.querySelector('.nav-filter .active a').click();
            }
        },

        toggleSidebar: function() {
            if (
                document
                    .querySelector('body')
                    .classList.contains('sidebar-filter-active')
            ) {
                document
                    .querySelector('body')
                    .classList.remove('sidebar-filter-active');
                document
                    .querySelector('#product-filter-area')
                    .classList.remove('active');
            } else {
                document
                    .querySelector('body')
                    .classList.add('sidebar-filter-active');
                document
                    .querySelector('#product-filter-area')
                    .classList.add('active');
            }
        },

        showSidebar: function() {
            document
                .querySelector('body')
                .classList.add('sidebar-filter-active');
            document
                .querySelector('#product-filter-area')
                .classList.add('active');
        },

        hideSidebar: function() {
            document
                .querySelector('body')
                .classList.remove('sidebar-filter-active');

            document
                .querySelector('#product-filter-area')
                .classList.remove('active');
        }
    }
};
</script>
