<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<template>
    <div>
      <div class="card  border-0 text-center w-100 rounded p-2">
        <div class="d-flex justify-content-center">
          <img :src="user.imageUrl" class="rounded-circle shadow"
          alt="avatar" width="100" height="100">
        </div>
        <div class="display-5 mt-2 h4">{{user.name}}</div>
        <div class="mt-2 text-secondary h5">Username: @{{user.username}}</div>
        <p class="fs-5 my-2">{{user.bio}}</p>
        <div class="text-center mb-2 mt-1">
          <a :href="'https://github.com/'+user.username" class="btn btn-primary" target="_blank">VIEW PROFILE</a>
        </div>
      </div>
      <div class="row mb-3 d-flex justify-content-center">
        <div class="col-xl-4 col-md-6 col-sm-12 mt-3">
          <div class="card shadow text-center border rounded py-3">
            <div class="h3 py-2 fw-normal">Repostitories</div>
            <div class="fs-5">{{user.noOfRepo}}</div>
          </div>
        </div>
        <div class="col-xl-4 col-md-6 col-sm-12 mt-3">
          <div class="card shadow text-center border rounded py-3">
            <div class="h3 py-2 fw-normal">Following</div>
            <div class="fs-5">{{user.following}}</div>
          </div>
        </div>
        <div class="col-xl-4 col-md-6 col-sm-12 mt-3">
          <div class="card shadow text-center border rounded py-3">
            <div class="h3 py-2 fw-normal">Followers</div>
            <div class="fs-5">{{user.followers}}</div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'UserProfile',
  props: {
    user: Object,
  },
};
</script>
