<template>
    <div class="Menu_Item" @click="isOpen = !isOpen">
      <a> {{ title }} </a>
      <transition name="fade_dropdown" appear>
      <div class="sub_menu" v-if="isOpen">
        <div v-for="(item, i) in items" :key="i" class="Menu_Item">
            <a :href="item.link">{{  item.title }}</a>
        </div>
      </div>
      </transition>
    </div>
</template>

<script>
export default {
    name: "dropdown",
    props: {
        title: {
            type: String,
            required: true
        },
        items: {
            type: Array,
            default: () => []
        }
    }, data() {
        return {
        isOpen: false
        };
    }
};
</script>

<style>
nav .Menu_Item svg {
    width: 10px;
    margin-left: 10px;
}

.fade_dropdown-enter-active,
.fade_dropdown-leave-active {
    transition: all .6s ease-out;
}

.fade_dropdown-enter,
.fade_dropdown-leave-to {
    opacity: 0;
}

nav .Menu_Item .sub_menu {
    position: absolute;
    background-color: var(--background_text);
    top: calc(100% + 5px);
    left: 50%;
    transform: translateX(-50%);
    width: max-content;
    border-radius: 0px 0px 20px 20px;
}
</style>