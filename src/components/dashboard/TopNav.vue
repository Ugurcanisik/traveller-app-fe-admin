<template>
  <div class="row page-inner mt--5">
    <div class="col-sm-6 col-md-3">
      <div class="card card-stats card-round">
        <div class="card-body ">
          <div class="row">
            <div class="col-5">
              <div class="icon-big text-center">
                <i class="flaticon-coins text-success"></i>
              </div>
            </div>
            <div class="col-7 col-stats">
              <div class="numbers">
                <p class="card-category">Günlük Ciro</p>
                <h4 class="card-title">{{ ciroYesterday  }}</h4>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-sm-6 col-md-3">
      <div class="card card-stats card-round">
        <div class="card-body ">
          <div class="row">
            <div class="col-5">
              <div class="icon-big text-center">
                <i class="flaticon-graph-2 text-info"></i>
              </div>
            </div>
            <div class="col-7 col-stats">
              <div class="numbers">
                <p class="card-category">Ortalama Ciro</p>
                <h4 class="card-title">{{ ciroAverage  }}</h4>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-sm-6 col-md-3">
      <div class="card card-stats card-round">
        <div class="card-body">
          <div class="row">
            <div class="col-5">
              <div class="icon-big text-center">
                <i class="flaticon-graph text-warning"></i>
              </div>
            </div>
            <div class="col-7 col-stats">
              <div class="numbers">
                <p class="card-category">Aylık Ciro</p>
                <h4 class="card-title">{{ ciroMonth  }}</h4>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-sm-6 col-md-3">
      <div class="card card-stats card-round">
        <div class="card-body">
          <div class="row">
            <div class="col-5">
              <div class="icon-big text-center">
                <i class="flaticon-network text-danger"></i>
              </div>
            </div>
            <div class="col-7 col-stats">
              <div class="numbers">
                <p class="card-category">Günlük Gider</p>
                <h4 class="card-title">{{ expenseToday }}</h4>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import {mapGetters} from "vuex";

export default {
  data() {
    return {
      ciroYesterday: null,
      ciroAverage: null,
      ciroMonth: null,
      expenseToday: null
    }
  },
  computed: {

  },
  mounted() {

  },
  watch: {

  },
}
</script>
