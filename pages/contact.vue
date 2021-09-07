<template>
    <div>
        <section id="hero2" class="section-bg">
        </section>
        <!-- ======= Contact Section ======= -->
        <section id="contact" class="contact">
      <div class="container">
        <div class="section-title">
          <h2>Contact</h2>
          <h3><span>Contact Us</span></h3>
        </div>
        <div class="row">
            <div class="col-lg-6 ">
                <div class="row">
                    <div class="col-lg-6">
                        <div class="info-box mb-4">
                            <i class="bx bx-map"></i>
                            <h3>PT. Groot Perkasa</h3>
                            <p>Jl. Lkr. Luar Barat No.1 Ciputra International (Tokopedia Care Tower) Lt.1 No. 02-06 Jakarta</p>

                            <h4>Phone</h4>
                            <p>+62 888888</p>
                            <h4>Email</h4>
                            <p></p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-lg-6">
                <form >
                    <div class="form-group">
                        <input type="text" v-model="contact.name" class="form-control" id="name" placeholder="Your Name" data-rule="minlen:4" data-msg="Please enter at least 4 chars" />
                        <div class="validate"></div> 
                    </div>
                    <div class="form-group">
                        <input type="email" class="form-control" v-model="contact.email" id="email" placeholder="Your Email" data-rule="email" data-msg="Please enter a valid email" />
                        <div class="validate"></div>
                    </div>
                    <div class="form-group">
                        <input type="text" class="form-control" v-model="contact.phone" id="phone" placeholder="Phone +62" data-rule="minlen:4" data-msg="Please enter at least 8 chars of phone" />
                        <div class="validate"></div>
                    </div>
                    <div class="form-group">
                        <textarea class="form-control" v-model="contact.message" rows="5" data-rule="required" data-msg="Please write something for us" placeholder="Message"></textarea>
                        <div class="validate"></div>
                    </div>
                    <div class="text-center"><button type="button" class="btn-get-started" @click="send">Send Message</button></div>
                </form>
            </div>

        </div>

      </div>
        </section>
        <!-- End Contact Section -->
    </div> 
</template>

<script>
import axios from 'axios'
import { domainApi } from '@/config'
export default {
  data () {
    return {
      contact: {
        name: null,
        email: null,
        phone: null,
        message: null
      }
    }
  },
  methods: {
    async send () {
      try {
        const response = await axios.post(domainApi + '/contacts', this.contact)
        console.log(response)
        this.contact = {
          name: null,
          email: null,
          phone: null,
          message: null
        }
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>
