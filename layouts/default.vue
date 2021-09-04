<template>
    <div>
        <!-- ======= Top Bar ======= -->
        <div id="topbar" class="d-none d-lg-flex align-items-center fixed-top">
            <div class="container d-flex">
                <div class="contact-info mr-auto">
                    <i class="icofont-envelope"></i> <a href="mailto:contact@example.com">contact@example.com</a>
                    <i class="icofont-phone"></i> +1 5589 55488 55
                </div>
                <div class="social-links">
                    <a href="#" class="twitter"><i class="icofont-twitter"></i></a>
                    <a href="#" class="facebook"><i class="icofont-facebook"></i></a>
                    <a href="#" class="instagram"><i class="icofont-instagram"></i></a>
                    <a href="#" class="skype"><i class="icofont-skype"></i></a>
                    <a href="#" class="linkedin"><i class="icofont-linkedin"></i></a>
                </div>
            </div>
        </div>
        <!-- ======= End Top Bar ======= -->
        <!-- ======= Header ======= -->
        <header id="header" class="fixed-top">
            <div class="container d-flex align-items-center">

            <h1 class="logo mr-auto"><a href="/">Groot<span>.</span></a></h1>
            <!-- Uncomment below if you prefer to use an image logo -->
            <!-- <a href="index.html" class="logo mr-auto"><img src="assets/img/logo.png" alt=""></a>-->

            <nav class="nav-menu d-none d-lg-block">
                <ul>
                <li class="active"><a href="/">Home</a></li>
                <li><a href="/about-us">About</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#portfolio">Portfolio</a></li>
                <li><a href="#team">Team</a></li>
                <li class="drop-down"><a href="">Drop Down</a>
                    <ul>
                    <li><a href="#">Drop Down 1</a></li>
                    <li class="drop-down"><a href="#">Deep Drop Down</a>
                        <ul>
                        <li><a href="#">Deep Drop Down 1</a></li>
                        <li><a href="#">Deep Drop Down 2</a></li>
                        <li><a href="#">Deep Drop Down 3</a></li>
                        <li><a href="#">Deep Drop Down 4</a></li>
                        <li><a href="#">Deep Drop Down 5</a></li>
                        </ul>
                    </li>
                    <li><a href="#">Drop Down 2</a></li>
                    <li><a href="#">Drop Down 3</a></li>
                    <li><a href="#">Drop Down 4</a></li>
                    </ul>
                </li>
                <li><a href="#contact">Contact</a></li>

                </ul>
            </nav><!-- .nav-menu -->

            </div>
        </header>
        <!-- End Header -->
        <!-- Content -->
        <Nuxt />
        <!-- End Content -->
        <section id="footer-header" class="d-flex align-items-center">
            <div class="container" data-aos="zoom-out" data-aos-delay="100">
                <h5>Working since 2017</h5>
                <h1>We are leader</h1>
                <h2>in Mechanical Building</h2>
            </div>
        </section>
        <!-- ======= Footer ======= -->
        <footer id="footer">
            <div class="footer-top">
                <div class="container">
                    <div class="row">

                    <div class="col-lg-3 col-md-6 footer-contact">
                        <h3>Groot Perkasa</h3>
                        <p>
                        Jl. Lkr. Luar Barat No.1 <br>
                        Ciputra International (Tokopedia Care Tower) Lt.1 No. 02-06<br>
                        Jakarta <br><br>
                        <strong>Phone:</strong> +62 859 <br>
                        <strong>Email:</strong> info@example.com<br>
                        </p>
                    </div>

                    <div class="col-lg-3 col-md-6 footer-links">
                        <h4>Useful Links</h4>
                        <ul>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Home</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">About us</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Services</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Terms of service</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Privacy policy</a></li>
                        </ul>
                    </div>

                    <div class="col-lg-3 col-md-6 footer-links">
                        <h4>Our Services</h4>
                        <ul>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Web Design</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Web Development</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Product Management</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Marketing</a></li>
                        <li><i class="bx bx-chevron-right"></i> <a href="#">Graphic Design</a></li>
                        </ul>
                    </div>

                    <div class="col-lg-3 col-md-6 footer-links">
                        <h4>Our Social Networks</h4>
                        <p>Cras fermentum odio eu feugiat lide par naso tierra videa magna derita valies</p>
                        <div class="social-links mt-3">
                            <a href="#" class="twitter"><i class="bx bxl-twitter"></i></a>
                            <a href="#" class="facebook"><i class="bx bxl-facebook"></i></a>
                            <a href="#" class="instagram"><i class="bx bxl-instagram"></i></a>
                            <a href="#" class="google-plus"><i class="bx bxl-skype"></i></a>
                            <a href="#" class="linkedin"><i class="bx bxl-linkedin"></i></a>
                        </div>
                    </div>

                    </div>
                </div>
            </div>
            <div class="container py-4">
                <div class="copyright">
                    &copy; Copyright <strong><span>PT Groot Perkasa</span></strong>. All Rights Reserved
                </div>
                <div class="credits">
                    <!-- All the links in the footer should remain intact. -->
                    <!-- You can delete the links only if you purchased the pro version. -->
                    <!-- Licensing information: https://bootstrapmade.com/license/ -->
                    <!-- Purchase the pro version with working PHP/AJAX contact form: https://bootstrapmade.com/bizland-bootstrap-business-template/ -->
                    Designed by <a href="h#">Pramanda Tirta Mulya</a>
                </div>
            </div>
        </footer>
        <!-- End Footer -->
    </div>
</template>

<script>
export default {
  methods: {
    handleScroll () {
      if(document.documentElement.scrollTop >= 150) {
        document.getElementById("header").classList.add('header-scrolled')
        document.getElementById("topbar").classList.add('topbar-scrolled')
      }else{
        document.getElementById("header").classList.remove('header-scrolled')
        document.getElementById("topbar").classList.remove('topbar-scrolled')
      }

    }
  },
  created () {
    if (process.browser) { 
        window.addEventListener('scroll', this.handleScroll);
    }
  },
  destroyed () {
    if (process.browser) { 
        window.removeEventListener('scroll', this.handleScroll);
    }
  }
}
</script>