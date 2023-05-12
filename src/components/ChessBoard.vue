<script setup>
import { ref } from "vue"

const emit = defineEmits(['chess-move']),
  alpha = ref(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']),
  digits = ref([8, 7, 6, 5, 4, 3, 2, 1]),
  row = ref(null),
  gameMoves = ref([])

const chessMove = ($event) => {
  gameMoves.value.push($event.target.id)
  $event.target.classList.toggle('active')
  emit('chess-move', JSON.parse(JSON.stringify(gameMoves.value)))
}
</script>

<template>
  <div class="card mt-5">
    <div class="card-body">
      <h5 class="card-title">Chess board</h5>

      <div class="chessboard">
        <div class="chessboard__alpha">
          <ul class="chessboard__alpha__list">
            <li v-for="char in alpha" class="chessboard__alpha__list__item">{{ char }}</li>
          </ul>
        </div>
        <div class="chessboard__nums">
          <ul class="chessboard__nums__list">
            <li v-for="num in digits" class="chessboard__nums__list__item">{{ num }}</li>
          </ul>
        </div>
        <div class="chessboard__main">
          <div class="chessboard__main__table">
            <div v-for="(char, i) in alpha" :key="i" class="chessboard__main__table__col">
              <div
                v-for="(num, j) in digits"
                :key="j"
                :class="{'white-cell': (i + j) % 2 == 0, 'black-cell': (i + j) % 2 != 0}"
                :id="`${char}-${num}`"
                ref="row"
                class="chessboard__main__table__col__row"
                @click="chessMove($event)" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
