<template>
  <div class="upload">
    <div class="upload_form">
      <h1 class="upload_form_title">Upload your image</h1>
      <p class="upload_form_note">File should be Jpeg, Png,...</p>
      <div class="upload_form_main">
        <figure
          class="-drop"
          :class="{ '-active': isDrag }"
          @dragenter="dragEnter"
          @dragleave="dragLeave"
          @dragover.prevent
          @drop.prevent="dropFile"
        >
          <img src="@/assets/img/image.svg" width="" height="" />
          <p class="-text">Drag & Drop your image here</p>
        </figure>
        <p class="-text">Or</p>
        <div class="-button">
          <label class="-label">
            Choose a file
            <input type="file" @change="uploaded" />
          </label>
        </div>
      </div>
    </div>
    <!-- アップロードアニメーション -->
    <!-- アップロード後 -->
    <div class="upload_loading">
      <p class="upload_loading_text">Uploading...</p>
      <div class="upload_loading_bar"><span class="-active"></span></div>
    </div>
  </div>
</template>

<script>
import firebase from '@/plugins/firebase'
export default {
  data() {
    return {
      isDrag: false,
    }
  },
  methods: {
    uploaded(photo) {
      // 選択されたファイルを取得
      const photoFile = photo.target.files[0]
      this.uploadFirebase(photoFile)
    },
    dragEnter() {
      console.log('now drag...')
      this.isDrag = true
    },
    dragLeave() {
      console.log('drag leave!')
      this.isDrag = false
    },
    dropFile() {
      // TODO ファイル取得
      this.isDrag = false
      const photoFile = event.dataTransfer.files[0]
      this.uploadFirebase(photoFile)
    },
    uploadFirebase(file) {
      const storageRef = firebase.storage().ref('images/' + file.name)
      // firebaseに画像アップロード
      storageRef.put(file).then(() => {
        console.log(file.name + 'が保存されました')
        // アップロードした画像のURLを表示
        storageRef.getDownloadURL().then((url) => {
          console.log(url)
        })
      })
    },
  },
}
</script>

<style lang="scss" scoped>
.upload {
  &_form {
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
      .-drop {
        padding: 36px 0 40px;
        background-color: #f6f8fb;
        border: 1px dashed #97bef4;
        box-sizing: border-box;
        border-radius: 12px;
        text-align: center;
        &.-active {
          border: 3px solid #97bef4;
        }
        .-text {
          padding-top: 37px;
          font-size: 1.2rem;
          line-height: 1.8rem;
          letter-spacing: -0.035em;
          color: #bdbdbd;
        }
      }
      .-text {
        padding-top: 18px;
        text-align: center;
        font-size: 1.2rem;
        line-height: 1.8rem;
        text-align: center;
        letter-spacing: -0.035em;
        color: #bdbdbd;
      }
      .-button {
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
  &_loading {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
    width: 400px;
    height: 143px;
    padding: 36px 27px 43px 32px;
    background: #fff;
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
    border-radius: 12px;
    &_text {
      font-family: Poppins;
      font-style: normal;
      font-weight: 500;
      font-size: 18px;
      line-height: 27px;
      letter-spacing: -0.035em;
      color: #4f4f4f;
    }
    &_bar {
      margin-top: 30px;
      width: 100%;
      height: 6px;
      background: #f2f2f2;
      border-radius: 8px;
      position: relative;
      overflow: hidden;
      .-active {
        position: absolute;
        top: 0;
        left: 0;
        width: 30%;
        height: 6px;
        background: #2f80ed;
        border-radius: 8px;
        // before
        // animation: loading 2s 0.5s linear infinite;
        // after
        animation: {
          name: loading;
          duration: 2s; // かかる時間
          delay: 0.5s; // 何秒後に開始するか
          timing-function: linear; // 速度 linear : 一定
          iteration-count: infinite; // 無限ループ
        }
      }
    }
  }
}
@keyframes loading {
  from {
    left: -100%;
  }
  to {
    left: 100%;
  }
}
</style>
