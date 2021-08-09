<template>
  <div class="x-videos">
    <div id="logo" class="logo-container">
      <div class="prefix" contenteditable @input="onPrefixInput">
        {{ prefixText }}
      </div>
      <div class="suffix" contenteditable @input="onSuffixInput">
        {{ suffixText }}
      </div>
    </div>

    <br />
    <button class="download" @click="download">Download</button>
  </div>
</template>

<script>
import { defineComponent, reactive, toRefs } from "vue";
import domToImage from "dom-to-image";
import downloadFile from "js-file-download";

export default defineComponent({
  name: "XVideos",
  setup() {
    const state = reactive({
      prefixText: "X",
      suffixText: "VIDEOS",
    });

    const onPrefixInput = (evt) => {
      state.prefixText = evt.target.childNodes[0].nodeValue;
    };

    const onSuffixInput = (evt) => {
      state.suffixText = evt.target.childNodes[0].nodeValue;
    };

    const download = () => {
      const node = document.getElementById("logo");
      domToImage.toBlob(node).then((blob) => {
        downloadFile(blob, "xvideos.png");
      });
    };

    return {
      ...toRefs(state),
      onPrefixInput,
      onSuffixInput,
      download,
    };
  },
});
</script>

<style lang="less" scoped>
.x-videos {
  display: inline-block;

  .logo-container {
    width: 470px;
    height: 110px;
    background: #010101;
    font-size: 80px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-family: sans-serif;
    border: 1px solid #333;
    border-radius: 5px;
    margin: 50px 0;

    .prefix,
    .suffix {
      padding: 0 5px;
    }

    .prefix {
      color: #e62506;
    }

    .suffix {
      color: #fefefe;
      letter-spacing: 4px;
    }
  }

  .download {
    width: 100px;
    height: 40px;
    border-radius: 3px;
    line-height: 38px;
    text-align: center;
    color: #010101;
    background: #fefefe;
    border: none;
  }
}
</style>
