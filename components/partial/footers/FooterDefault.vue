<template>
    <footer class="footer footer-2">
        <div class="footer-bottom">
            <div :class="isFullwidth ? 'container-fluid' : 'container'">
                <p class="footer-copyright">Copyright © 2021 Molla Store. All Rights Reserved.</p>

                <ul class="footer-menu">
                    <li>
                        <a href="#">Terms Of Use</a>
                    </li>
                    <li>
                        <a href="#">Privacy Policy</a>
                    </li>
                </ul>

                <div class="social-icons social-icons-color">
                    <a
                        href="#"
                        class="social-icon social-facebook"
                        title="Facebook"
                        target="_blank"
                    >
                        <i class="icon-facebook-f"></i>
                    </a>
                    <a href="#" class="social-icon social-twitter" title="Twitter" target="_blank">
                        <i class="icon-twitter"></i>
                    </a>
                    <a
                        href="#"
                        class="social-icon social-instagram"
                        title="Instagram"
                        target="_blank"
                    >
                        <i class="icon-instagram"></i>
                    </a>
                    <a href="#" class="social-icon social-youtube" title="Youtube" target="_blank">
                        <i class="icon-youtube"></i>
                    </a>
                    <a
                        href="#"
                        class="social-icon social-pinterest"
                        title="Pinterest"
                        target="_blank"
                    >
                        <i class="icon-pinterest"></i>
                    </a>
                </div>
            </div>
        </div>
        <div class="mb-10" v-if="bottomSticky"></div>
	</footer>
</template>

<script>
export default {
    data: function () {
        return {
            bottomSticky: false
        }
    },
    computed: {
        isFullwidth: function() {
            return this.$route.path.includes('fullwidth');
        }
    },
    watch: {
        $route: function () {
            this.handleBottomSticky();
        }
    },
    mounted: function() {
        this.handleBottomSticky();
        window.addEventListener('resize', this.handleBottomSticky, {passive: true});
    },
    destroyed: function () {
        window.removeEventListener('resize', this.handleBottomSticky);
    },
    methods: {
        handleBottomSticky: function () {
            this.bottomSticky = this.$route.path.includes('/product/default') && (window.innerWidth > 991);
        }
    }
};
</script>