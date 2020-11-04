<template>
  <div class="uploadForm">
    <h1 class="uploadForm_title">Upload your image</h1>
    <p class="uploadForm_note">File should be Jpeg, Png,...</p>
    <div class="uploadForm_main">
      <figure class="uploadForm_main_drop">
        <img src="@/assets/img/image.svg" width="" height="" />
        <p class="-text">Drag & Drop your image here</p>
      </figure>
      <p class="uploadForm_main_text">Or</p>
      <div class="uploadForm_main_button">
        <label class="-label">
          Choose a file
          <input type="file" />
        </label>
      </div>
    </div>
  </div>
</template>

<script>
// import firebase from '@/plugins/firebase'
export default {
  data() {
    return {
      fileList: '',
    }
  },
}
</script>

<style lang="scss" scoped>
.uploadForm {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  width: 402px;
  height: 469px;
  background: #fff;
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
  border-radius: 12px;
  box-sizing: border-box;
  padding: 36px 3%;
  &_title {
    font-size: 1.8rem;
    font-weight: 500;
    line-height: 2.7rem;
    letter-spacing: -0.035em;
    color: #4f4f4f;
    text-align: center;
  }
  &_note {
    padding-top: 16px;
    font-weight: 500;
    font-size: 10px;
    line-height: 15px;
    text-align: center;
    letter-spacing: -0.035em;
    color: #828282;
  }
  &_main {
    padding-top: 30px;
    &_drop {
      padding: 36px 0 40px;
      background-color: #f6f8fb;
      border: 1px dashed #97bef4;
      box-sizing: border-box;
      border-radius: 12px;
      text-align: center;
      .-text {
        padding-top: 37px;
        font-size: 1.2rem;
        line-height: 1.8rem;
        letter-spacing: -0.035em;
        color: #bdbdbd;
      }
    }
    &_text {
      padding-top: 18px;
      text-align: center;
      font-size: 1.2rem;
      line-height: 1.8rem;
      text-align: center;
      letter-spacing: -0.035em;
      color: #bdbdbd;
    }
    &_button {
      padding-top: 21px;
      text-align: center;
      .-label {
        display: inline-block;
        cursor: pointer;
        padding: 8px 16px;
        background: #2f80ed;
        border-radius: 8px;
        font-weight: 500;
        font-size: 1.2rem;
        line-height: 1.6rem;
        text-align: center;
        letter-spacing: -0.035em;
        color: #fff;
        &:hover {
          opacity: 0.7;
          transition: 0.3s;
        }
        input {
          display: none;
        }
      }
    }
  }
}
</style>
