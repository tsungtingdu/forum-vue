<template>
  <div class="row">
    <div class="col-md-12 mb-3">
      <h1>{{ restaurant.name }}</h1>
      <p class="badge badge-secondary mt-1 mb-3">{{ restaurant.name }}</p>
    </div>
    <div class="col-lg-4">
      <img
        class="img-responsive center-block"
        :src="restaurant.image"
        style="width: 250px;margin-bottom: 25px;"
      />
      <div class="contact-info-wrap">
        <ul class="list-unstyled">
          <li>
            <strong>Opening Hour:</strong>
            {{ restaurant.opening_hours }}
          </li>
          <li>
            <strong>Tel:</strong>
            {{ restaurant.tel }}
          </li>
          <li>
            <strong>Address:</strong>
            {{ restaurant.address }}
          </li>
        </ul>
      </div>
    </div>
    <div class="col-lg-8">
      <p>{{ restaurant.description }}</p>
      <a class="btn btn-outline-info btn-border mr-2 btn-sm" href="#">Dashboard</a>

      <button
        v-if="restaurant.isFavorited"
        type="button"
        class="btn btn-danger btn-sm btn-border mr-2"
        @click.stop.prevent="deleteFavorite"
      >Remove from Favorite</button>
      <button
        v-else
        type="button"
        class="btn btn-primary btn-sm btn-border mr-2"
        @click.stop.prevent="addFavorite"
      >Add to Favorite</button>
      <button
        v-if="restaurant.isLiked"
        type="button"
        class="btn btn-danger btn-sm like mr-2"
        @click.stop.prevent="deleteLike"
      >Unlike</button>
      <button
        v-else
        type="button"
        class="btn btn-primary btn-sm like mr-2"
        @click.stop.prevent="addLike"
      >Like</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialRestaurant: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      restaurant: this.initialRestaurant
    };
  },
  methods: {
    addFavorite() {
      this.restaurant = {
        ...this.restaurant,
        isFavorited: true
      };
    },
    deleteFavorite() {
      this.restaurant = {
        ...this.restaurant,
        isFavorited: false
      };
    },
    addLike() {
      this.restaurant = {
        ...this.restaurant,
        isLiked: true
      };
    },
    deleteLike() {
      this.restaurant = {
        ...this.restaurant,
        isLiked: false
      };
    }
  }
};
</script>