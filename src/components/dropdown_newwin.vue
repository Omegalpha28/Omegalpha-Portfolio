<template>
    <div class="Menu_Item" @click="isOpen = !isOpen">
      <a> {{ title }} </a>
      <transition name="fade_dropdownN" appear>
        <div class="sub_menu" v-if="isOpen">
          <div v-for="(item, i) in items" :key="i" class="Menu_Item">
            <a :href="item.link" target="_blank">{{ item.title }}</a>
          </div>
        </div>
      </transition>
    </div>
</template>

<script>
  export default {
    name: "dropdown_newwin",
    props: {
      title: { // Changement de 'title_nw' à 'title'
        type: String,
        required: true
      },
      items: { // Changement de 'items_nw' à 'items'
        type: Array,
        default: () => []
      }
    },
    data() {
      return {
        isOpen: false
      };
    }
  };
  </script>

<style>
  .fade_dropdownN-enter-active,
  .fade_dropdownN-leave-active {
    transition: all .6s ease-out;
  }
  .fade_dropdownN-enter,
  .fade_dropdownN-leave-to {
    opacity: 0;
  }
  </style>
