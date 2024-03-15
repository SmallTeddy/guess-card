<template>
  <div h-screen flex-center color-gray>
    <div v-for="num in 10" :key="num">
      <div v-for="col in ['黑桃', '红桃', '梅花', '方块']" :key="col">
        <img :src="getCard(col as CardType, num as CardNum)" :alt="col + num">
      </div>
    </div>
  </div>
</template>

<script lang='ts' setup>
import { getAssetsFile } from '@/utils/index'

type CardType = '黑桃' | '红桃' | '梅花' | '方块'
type CardNum = 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10
type CardColor = 'S' | 'H' | 'C' | 'D'
const cardMap: Record<CardType, CardColor> = {
  '黑桃': 'S',
  '红桃': 'H',
  '梅花': 'C',
  '方块': 'D',
}

const getCard = (cardType: CardType, num: CardNum): string => {
  const card = cardMap[cardType] + num
  const cardAsset = `card/${card}.png`
  return getAssetsFile(cardAsset)
}
</script>

<style scoped></style>
