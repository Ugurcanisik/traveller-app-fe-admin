<template>
  <b-modal ref="updateProduct" title="Ürün Güncelle" hide-footer>
    <div class="modal-content">
      <div class="modal-body">


        <div class="form-group form-floating-label">
          <input
              id="picture"
              v-model="updateProduct.picture"
              type="text" class="form-control input-border-bottom" required>
          <label for="picture" class="placeholder">Resim</label>
        </div>


        <div class="form-group form-floating-label" :class="{'has-error': $v.updateProduct.name.$error}">
          <input
              id="productName"
              v-model="$v.updateProduct.name.$model"
              type="text" class="form-control input-border-bottom" required>
          <label for="productName" class="placeholder">Ürün Adı</label>
        </div>

        <div class="form-group form-floating-label">
          <input
              id="prodcutDescription"
              v-model="$v.updateProduct.description.$model"
              type="text" class="form-control input-border-bottom" required>
          <label for="prodcutDescription" class="placeholder">Ürün Açıklaması</label>
        </div>


        <div class="form-group form-floating-label" :class="{'has-error': $v.updateProduct.categoryId.$error}">
          <b-form-select
              class="form-control input-border-bottom"
              v-model="$v.updateProduct.categoryId.$model"
              :options="listCategory()"
          ></b-form-select>
        </div>

      </div>
      <div class="modal-footer no-bd" style="margin: 0 auto">
        <b-button variant="primary" @click="update" :disabled="$v.updateProduct.$invalid">Güncelle</b-button>
        <b-button variant="danger" @click="closeModal">Kapat</b-button>
      </div>
    </div>
  </b-modal>
</template>
<script>
import {mapGetters} from "vuex";
import {required} from "vuelidate/lib/validators";

export default {
  data() {
    return {
      updateProduct: {
        name: null,
        description: null,
        price: null,
        categoryId: null,
        picture: null
      },
      id: null
    }
  },
  methods: {
    closeModal() {
      this.$refs['updateProduct'].hide()
    },
    update() {
      this.$store.dispatch('loading', true)
      const updateProduct = {
        id: this.id,
        data: {
          name: this.updateProduct.name,
          description: this.updateProduct.description,
          category: this.updateProduct.categoryId,
          picture: this.updateProduct.picture
        }
      }
      this.$store.dispatch("updateTravel", updateProduct)
          .then(response => {
            if (response) {
              this.$refs['updateProduct'].hide()
              this.$store.dispatch('loading', false)
              this.$store.dispatch('alert', 'success')
            } else {
              this.$store.dispatch('loading', false)
              this.$store.dispatch('alert', 'error')
            }
          })
    },
    listCategory() {
      const category = this.allCategories
      let categoryArray = []

      categoryArray.push({value: null, text: 'Ürün Kategorisi Seçiniz'})

      for (let i in category) {
        categoryArray.push({value: category[i].id, text: category[i].name})
      }

      return categoryArray

    }
  },
  computed: {
    ...mapGetters(['getTravelModal']),
    ...mapGetters(["allCategories"]),
  },
  watch: {
    getTravelModal(payload) {
      this.updateProduct.name = payload[0].name
      this.updateProduct.description = payload[0].description
      this.updateProduct.categoryId = payload[0].category.id
      this.updateProduct.picture = payload[0].picture
      this.id = payload[0].id
      this.$refs['updateProduct'].show()
    }
  },
  validations: {
    updateProduct: {
      name: {required},
      description: {},
      categoryId: {required}
    }
  }
}
</script>
