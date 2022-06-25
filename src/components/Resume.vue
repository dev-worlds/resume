<template>
  <div class="container column">
    <form class="card card-w30">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="text"></textarea>
      </div>
      <button class="btn primary" :disabled="text.length <= 3" @click.prevent="handleCLickCreate">Добавить</button>
    </form>

    <div class="card card-w70">
      <template v-if="blockList.length">
        <template v-for="(block, index) in blockList" :key="index">
          <component :is="block.type + '-block'" :text="block.text"></component>
        </template>
      </template>
      <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
  </div>
</template>

<script>
import TextBlock from "@/components/TextBlock";
import TitleBlock from "@/components/TitleBlock";
import SubtitleBlock from "@/components/SubtitleBlock";
import AvatarBlock from "@/components/AvatarBlock";

export default {
  name: "Resume",
  components: {
    TextBlock,
    TitleBlock,
    SubtitleBlock,
    AvatarBlock
  },
  data() {
    return {
      type: 'title',
      text: '',
      blockList: [],
    }
  },
  methods: {
    handleCLickCreate() {
      if (this.type && this.text.length > 3) {
        this.addBlock();
        this.resetForm();
      }
    },
    addBlock() {
      this.blockList.push({
        type: this.type,
        text: this.text
      });
    },
    resetForm() {
      this.type = 'title';
      this.text = '';
    },
  },
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>