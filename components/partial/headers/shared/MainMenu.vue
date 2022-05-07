<template>
    <nav class="main-nav">
        <ul class="menu sf-arrows">
          <li :class="{active: current=='home'}">
            <nuxt-link to="/">Accueil</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/shop/nosidebar/boxed">Produits</nuxt-link>

          </li>
          <li>
            <nuxt-link to="/shop/checkout">Checkout</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/shop/dashboard">My Account</nuxt-link>
          </li>
            <li :class="{active: current=='product'}">
                <nuxt-link
                    to="/product/default/dark-yellow-lace-cut-out-swing-dress"
                >Show Product</nuxt-link>
            </li>
            <li :class="{active: current=='pages'}">
                <a href="javascript:;" class="sf-with-ul">Pages</a>

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
            <li :class="{active: current=='blog'}">
                <nuxt-link to="/blog/classic" class="sf-with-ul">Blog</nuxt-link>
                <ul>
                  <li>
                    <nuxt-link to="/blog/grid/grid-2">Grid 2 columns</nuxt-link>
                  </li>
                  <li>
                    <nuxt-link
                        to="/blog/single/sidebar/utaliquam-sollicitzdvudin-leo"
                    >Fullwidth with sidebar</nuxt-link>
                  </li>
                </ul>
            </li>
        </ul>
    </nav>
</template>
<script>
export default {
    computed: {
        current: function() {
            if (this.$route.path.includes('elements')) return 'elements';
            if (this.$route.path.includes('shop')) return 'shop';
            if (this.$route.path.includes('blog')) return 'blog';
            if (this.$route.path.includes('product')) return 'product';
            if (this.$route.path.includes('pages')) return 'pages';
            return '/';
        }
    },
    methods: {
        viewAllDemos: function(e) {
            var list = document.querySelectorAll('.demo-list .hidden');
            for (let i = 0; i < list.length; i++) {
                list[i].classList.add('show');
            }

            e.currentTarget.parentElement.classList.add('d-none');
        }
    }
};
</script>
