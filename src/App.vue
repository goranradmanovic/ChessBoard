<script setup>
import { ref } from "vue"
import SideBar from './components/SideBar.vue'
import ChessBoard from './components/ChessBoard.vue'

const chessMoves = ref([])

const getChessMoves = (payload) => {
  chessMoves.value = payload;
}
</script>

<template>
  <main>
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-8 col-md-12 col-sm-12">
          <ChessBoard @chess-move="getChessMoves" />
        </div>
        <div class="col-lg-4 col-md-12 col-sm-12">
          <SideBar :chessmoves="chessMoves" />
        </div>
      </div>
    </div>
  </main>
</template>
