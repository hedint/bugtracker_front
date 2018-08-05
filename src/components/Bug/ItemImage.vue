<template>
  <div :class="getClass">
    <div class="bug-table-item__image-list-item"
    v-for="image in getImages"
    :key="image"
    @click="showImage(image)">
      <img :src="image" />
    </div>
    <OverlayPopup v-if="current_image" @overlayClick="closePopup">
      <div class="bug-table-item__image-full">
        <img :src="current_image"/>
      </div>
    </OverlayPopup>
  </div>
</template>
<script>
import OverlayPopup from '../common/OverlayPopup';
export default {
  name: "ItemImage",
  props: {
    id: String,
    images: [Array, String],
  },
  data () {
    return {
          current_image: false
    }
  },
  computed: {
    getImages() {
      if (typeof this.images === "string") {
        return [this.images];
      }
      return this.images;
    },
    getClass() {
      return `bug-table-item__${this.id}`;
    }
  },
  methods: {
    showImage(image) {
      this.current_image = image;
    },
    closePopup () {
      this.current_image = false;
    }
  },
  components : {
    OverlayPopup
  },
  mounted () {
    console.log(this.current_image);
  }
};
</script>