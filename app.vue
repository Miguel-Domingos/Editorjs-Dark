<template>
  <div class="dark w-screen h-screen">
    <div class="flex flex-col pt-20 gap-8">
      <div class="w-full flex justify-center">
        <h1 class="dark:text-white font-semibold text-3xl text-slate-900">
          EditorJS Dark-mode
        </h1>
      </div>
      <div class="container mx-auto">
        <div id="editor"></div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import EditorJS from "@editorjs/editorjs";
import Header from "@editorjs/header";
import List from "@editorjs/list";
import { onMounted, ref } from "vue";

const editor = new EditorJS({
  holder: "editor",
  placeholder: "Start building your Project here, write...",
  // autofocus: true,
  inlineToolbar: true,
  // readOnly: true,
  tools: {
    header: {
      class: Header,
      inlineToolbar: ["link"],
    },
    list: {
      class: List,
      inlineToolbar: true,
    },
  },
  data: { blocks: [] },
});

onMounted(() => {
  editor;
});
</script>

<style>
:root {
  /* background color */
  --main: #111827;

  /* Toolbar and popover */
  --primary: #0f172a;

  /* On hover or selected */
  --selected: rgba(255, 255, 255, 0.2);

  /* Border color */
  --border: #1e293b;

  /* Text and icon colors */
  --text: white;
}

* {
  padding: 0;
  margin: 0;
  font-family: sans-serif;
}
.dark {
  background-color: var(--main);
}

.dark .ce-toolbar__plus,
.dark .ce-toolbar__settings-btn,
.dark .ce-popover-item__title,
.dark .ce-popover-item__icon {
  color: var(--text);
}

.dark .cdx-search-field.ce-popover__search {
  background-color: #1e293b4d;
  border-color: var(--border);
}

.dark .cdx-search-field__input {
  color: var(--text);
}

.dark .cdx-block,
.dark .ce-block {
  color: var(--text);
}

.dark .ce-inline-toolbar,
.dark .ce-conversion-tool__icon,
.dark .ce-popover-item__icon {
  color: var(--text);
  background-color: var(--primary);
  border-color: var(--border);
}

.dark .ce-popover,
.dark .ce-conversion-toolbar,
.dark .ce-inline-toolbar {
  background-color: var(--primary);
  border-color: var(--border);
  box-shadow: 0 3px 15px -3px var(--border);
}

.dark .ce-inline-tool:hover,
.dark .ce-inline-toolbar__dropdown:hover,
.dark .ce-toolbar__plus:hover,
.dark .ce-toolbar__settings-btn:hover,
.dark .ce-conversion-tool:hover,
.dark .ce-popover-item:hover {
  background-color: var(--selected);
}

.dark .ce-block .ce-block__content *::selection,
.dark .cdx-block *::selection,
.dark .cdx-search-field__input::selection,
.dark .ce-block.ce-block--selected .ce-block__content {
  background-color: var(--selected);
}

@media (max-width: 650px) {
  .dark .ce-toolbar__settings-btn,
  .dark .ce-toolbar__plus {
    background-color: var(--primary);
    border-color: var(--border);
    box-shadow: 0 3px 15px -3px var(--border);
  }
}
</style>
