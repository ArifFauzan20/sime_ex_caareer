<template>
  <!-- Page Title
  =============================================-->
  <section id="page-title" class="nobg">
    <div class="container clearfix">
      <h1>Careers</h1>
      <ol class="breadcrumb">
        <li class="breadcrumb-item"><a href="#">Home</a></li>
        <li class="breadcrumb-item" aria-current="page">Careers</li>
      </ol>
    </div>
  </section>
  <!-- #page-title end -->
  <!-- Content
		============================================= -->
  <section id="content">
    <div class="content-wrap">
      <div class="container">
        <div class="ro" style="max-width: 2400px">
          <div class="col-lg-12">
            <div class="heading-block center">
              <h3 class="notranslate">Simetri Job Career</h3>
              <span
                >How we do things resonates with you, we welcome you to join
                us.</span
              >
            </div>
            <!-- accordion -->
            <div class="container row">
              <div class="accordion accordion-flush" id="app">
                <div
                  class="accordion-item"
                  v-for="(career, id) in career"
                  :key="id"
                >
                  <h2 class="accordion-header" :id="career.id_career">
                    <button
                      class="accordion-button collapsed fw-bold notranslate"
                      type="button"
                      data-bs-toggle="collapse"
                      :data-bs-target="'#flush-collapseOne' + career.id_career"
                      aria-expanded="false"
                      aria-controls="flush-collapseOne"
                      style=""
                    >
                      {{ career.nama_career }}
                    </button>
                  </h2>
                  <div
                    :id="'flush-collapseOne' + career.id_career"
                    class="accordion-collapse collapse"
                    :aria-labelledby="career.id_career"
                    data-bs-parent="#app"
                    style=""
                  >
                    <div class="accordion-body">
                      <div class="row">
                        <div
                          class="col-md-6 text-start"
                          style="padding: 10px 0px 0px 30px; dispaly: block"
                        >
                          <p><strong>Job Description:</strong></p>
                          <p v-html="career.desc_career"></p>
                        </div>
                        <div
                          class="col-md-6 text-start"
                          style="padding: 10px 0px 0px 30px; dispaly: block"
                        >
                          <p><strong>Job Requirements:</strong></p>
                          <p v-html="career.require_career"></p>
                        </div>
                      </div>

                      <a
                        class="
                          btn btn-hero btn-sm btn-rounded btn-noborder
                          notranslate
                        "
                        style="background: rgb(8, 66, 124); color: #e8e8e8"
                        :href="'mailto:' + career.email_career"
                        >Apply Now</a
                      >
                    </div>
                  </div>
                </div>
              </div>
              <!-- left side -->
              <!-- <div class="col-md-4">
                <div class="" style="width: auto; padding: 5px, 5px, 0px, 0px">
                  <div class="card-body">
                    <h5 class="card-title" style="font-size: 18px">
                      Keuntungan
                    </h5>
                    <hr />
                    <h6 class="card-subtitle mb-4 text-muted"></h6>

                    <ul class="card-text text-start list-bullet">
                      <li class="listku">Gaji yang menarik</li>
                      <li class="listku">
                        Komisi menarik untuk posisi sales dan marketing
                      </li>
                      <li class="listku">Bonus tahunan</li>
                      <li class="listku">BPJS</li>
                      <li class="listku">
                        Jaminan kesehatan, gigi, dan kacamata
                      </li>
                      <li class="listku">
                        Lorem ipsum dolor sit amet, consectetur adipisicing
                        elit. Beatae sint natus voluptas iste distinctio modi
                        vel laboriosam dolore ab? Autem necessitatibus dolor
                        nemo quam ratione obcaecati ab velit ullam asperiores.
                      </li>
                      <li class="listku">Asuransi jiwa</li>
                      <li class="listku">
                        Disability plans, including sick pay
                      </li>
                      <li class="listku">Cuti</li>
                      <li class="listku">Bantuan relokasi</li>
                    </ul>
                  </div>
                </div>
              </div> -->
            </div>

            <!-- accordion end -->
            <div id="faqs-list">
              <div class="row align-items-stretch grid-border clearfix"></div>
            </div>
          </div>
        </div>
      </div>

      <div class="line"></div>

      <!--  -->
    </div>
  </section>
  <!-- #content end -->
</template>
<script>
import { onMounted, ref } from "vue";
import axios from "axios";
export default {
  setup() {
    let career = ref([]);

    onMounted(() => {
      axios
        // .get("https://admin-sinarmetrindo.airartikennels.co.id/api/show_career")
        .get("http://127.0.0.1:8000/api/show_career")
        .then((result) => {
          career.value = result.data;
        })
        .catch((err) => {
          console.log(err.response);
        });
    });
    return {
      career,
    };
  },
};
</script>
<style>
.accordion-button {
  font-size: 18px;
}

.accordion-item {
  border: 1px solid rgba(35, 65, 100, 0.15);
}

.accordion-button:not(.collapsed) {
  color: inherit;
  background: rgb(8, 66, 124);
  color: #e8e8e8;
}
.listku {
  margin-bottom: 6px;
  color: rgb(8, 66, 124);
  margin-left: 6px;
  font-size: 12px;
  text-align: justify;
}
.fa {
  color: rgb(8, 66, 124);
  margin-right: 4px;
}
</style>