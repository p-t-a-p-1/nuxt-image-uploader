<template>
  <div class="uploadForm">
    <h1 class="upload_title">Upload your image</h1>
    <p class="upload_note">File should be Jpeg, Png,...</p>
    <div class="upload_main">
      <figure class="upload_main_drop">
        <img src="@/assets/img/image.svg" width="" height="" />
        <p class="-text">Drag & Drop your image here</p>
      </figure>
      <p class="upload_main_text">Or</p>
      <div class="upload_main_button">
        <label class="-label">
          Choose a file
          <input type="file" />
        </label>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.upload {
  &_title {
    font-size: 1.8rem;
  }
}
</style>
