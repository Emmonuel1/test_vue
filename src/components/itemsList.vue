<template>
    <div class="vertical-container">
      <div v-for="(item, index) in items" :key="index" class="vertical-item">
        <div class="square-item" v-for="(subitem, subindex) in item.subitems" :key="subindex" @mouseover="animateItem(subindex)">
          {{ subitem.value }}
        </div>
      </div>
    </div>
  </template>
  
<script lang="ts">
    import { defineComponent } from "vue";

    interface SubItem {
        value: number;
        animated: boolean;
    }

    interface Item {
        subitems: SubItem[];
    }

    export default defineComponent({
        data() {
            return {
                items: [] as Item[],
            };
        },
        mounted() {
            this.generateItems();
        },
        methods: {
            generateItems() {
            for (let i = 0; i < 110; i++) {
                const subitems: SubItem[] = [];
                const subitemsCount = Math.floor(Math.random() * 15) + 15;
                for (let j = 0; j <= subitemsCount; j++) {
                    subitems.push({ value: Math.floor(Math.random() * 100), animated: false });
                }
                this.items.push({ subitems });
            }
            },
            animateItem(index: number) {
            this.items.forEach(item => {
                item.subitems[index].animated = !item.subitems[index].animated;
            });
            },
        },
    });
</script>
  
<style scoped>

.vertical-container {
    display: flex;
    flex-direction: column; 
    height: 100vh;
}

.vertical-item {
    display: flex;
    flex-direction: row; 
}

.square-item {
    min-width: 50px;
    height: 50px;
    border: 1.5px solid black;
    border-radius: 10px;
    margin: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: transform 0.3s;
}

.square-item:hover {
    transform: scale(0.8);
}
</style>

<style> 

html, body {
    margin: 0;
}

*{
    box-sizing: border-box;
}

</style>
