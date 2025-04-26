<template>
  <div :class="['fold', position]" @click="handleClick">
    <div :class="['triangle',position]"></div>
    </div>
</template>

<script setup>
const emit = defineEmits(['flip', 'back'])

const props = defineProps({
    position: {
        type: String,
        default: 'bottom-right'
    }
})

const handleClick = () => {
    if (props.position === 'bottom-right') {
        emit('flip')
    } else {
        emit('back')
    }
}
</script>

<style scoped>
.fold {
  position: absolute;
  width: 60px;
  height: 60px;
  z-index: 20;
  cursor: pointer;
  pointer-events: auto;
}

.fold.bottom-right {
  bottom: 0;
  right: 0;
}

.fold.bottom-left {
  bottom: 0;
  left: 0;
}

.triangle {
  position: absolute;
  width: 0;
  height: 0;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.triangle.bottom-right {
  border-bottom: 50px solid transparent;
  border-left: 50px solid rgba(245, 245, 220, 0.78); 
  bottom: 0;
  right: 0;
}

.triangle.bottom-left {
  border-bottom: 50px solid transparent;
  border-right: 50px solid rgba(245, 245, 220, 0.78);
  bottom: 0;
  left: 0;
}


.fold.bottom-right:hover .triangle.bottom-right {
  transform: translate(-3px, -3px) rotate(-2deg);
  box-shadow: -2px -2px 5px rgba(0, 0, 0, 0.2);
}


.fold.bottom-left:hover .triangle.bottom-left {
  transform: translate(3px, -3px) rotate(2deg);
  box-shadow: 2px -2px 5px rgba(0, 0, 0, 0.2);
}
</style>