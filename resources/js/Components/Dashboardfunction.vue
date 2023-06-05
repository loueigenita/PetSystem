<template>
   <h1 class="text-4xl font-bold mt-5 text-center">DASHBOARD</h1>
  <div class="content-wrapper mt-5">
    <div class="container-fluid">
      <div class="row justify-center">
        <div class="col-lg-4 col-md-6">
          <div class="small-box bg-info">
            <div class="inner">
              <h3 class="text-4xl">{{ petCount }}</h3>
              <p class="mt-2 text-xl">Pets</p>
            </div>
            <div class="icon text-dark">
              <i class="fas fa-book"></i>
            </div>
            <a :href="route('pets.index')" class="small-box-footer">More info <i
                class="fas fa-arrow-circle-right"></i></a>
          </div>
        </div>

        <div class="col-lg-4 col-md-6 text">
          <div class="small-box bg-success">
            <div class="inner">
              <h3 class="text-4xl">{{ countUser }}</h3>
              <p class="mt-2 text-xl">Users</p>
            </div>
            <div class="icon text-dark">
              <i class="fas fa-users"></i>
            </div>
            <a :href="route('users')" class="small-box-footer">More info <i class="fas fa-arrow-circle-right"></i></a>
          </div>
        </div>

        <div class="col-lg-4 col-md-6">
          <div class="small-box bg-warning">
            <div class="inner">
              <h3 class="text-4xl">{{ countUser }}</h3>
              <p class="mt-2 text-xl">Visitors</p>
            </div>
            <div class="icon text-dark">
              <i class="fas fa-users"></i>
            </div>
            <a :href="route('users')" class="small-box-footer">More info <i class="fas fa-arrow-circle-right"></i></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { usePage } from '@inertiajs/vue3';
//   import { a } from '@inertiajs/vue3'

export default {
  setup() {
    const { props } = usePage();
    const petCount = props.petCount;
    const countUser = props.countUser;

    // Other component logic

    return {
      petCount,
      countUser,
    };
  },
};
</script>
<style>
.content {
  margin-top: 5rem;
}

.container-fluid {
  max-width: 100%;
  padding-right: 1rem;
  padding-left: 1rem;
  margin-right: auto;
  margin-left: auto;
}

.row {
  margin-right: -0.5rem;
  margin-left: -0.5rem;
}

.col-lg-4,
.col-md-6 {
  padding-right: 0.5rem;
  padding-left: 0.5rem;
}

.small-box {
  display: block;
  position: relative;
  box-sizing: border-box;
  margin-bottom: 1rem;
  border-radius: 0.25rem;
  background-color: #f8f9fa;
  border: 1px solid #f8f9fa;
  color: #333;
}

.small-box .inner {
  padding: 1.5rem;
}

.small-box h3 {
  font-size: 2rem;
  font-weight: 600;
  margin: 0 0 1rem 0;
  white-space: nowrap;
  color: #333;
}

.small-box p {
  margin: 0;
  font-weight: 500;
  color: #333;
}

.small-box .icon {
  position: absolute;
  top: -0.5rem;
  right: -0.5rem;
  z-index: 0;
  display: block;
  width: 4.5rem;
  height: 4.5rem;
  text-align: center;
  font-size: 3rem;
  line-height: 4.5rem;
  background-color: rgba(0, 0, 0, 0.15);
  border-radius: 50%;
  color: #fff;
}

.small-box .icon i {
  line-height: inherit;
}

.small-box a {
  position: absolute;
  bottom: 0;
  right: 0;
  color: rgba(255, 255, 255, 0.8);
  background-color: rgba(0, 0, 0, 0.1);
  padding: 0.75rem;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.875rem;
  border-top-left-radius: 0.25rem;
}</style>
  