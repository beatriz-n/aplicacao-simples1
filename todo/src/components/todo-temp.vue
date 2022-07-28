<template>
 <div class="tile flex-centered">
    <div class="titl-icon">
        <i class="icon icon-time"></i>
    </div>
        <dir class="tile-content">
            <div class="tile-subtitle">{{todo.description}}</div>
        </dir>
        <div class="tile-action">
            <button class="btn btn-link">Concluir</button>
            <button class="btn btn-link">
                <span class="text-error">Remover</span>
            </button>
        </div>
    </div>
</template>
<script>
export default {
  props: {
    todo: { type: Object, required: true }
  }
}
</script>
