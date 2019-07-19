<template>
  <div class="modal-card" ref="root">
    <header class="modal-card-head">
      <p class="modal-card-title">游戏规则</p>
    </header>
    <section class="modal-card-body">
      <h2 class="title">游戏模式</h2>
      <p>模式可以影响游戏体验和最终得分</p>

      <hr />

      <div class="columns is-mobile">
        <div class="column">
          <h3 class="subtitle">
            <b-icon icon="baby-buggy" />简单模式
          </h3>
          <p>开始练习</p>
          <p>时间因所选模式而有所不同。</p>
          <p></p>
          <p>在这个模式上玩你会失去50％的基本分数，在轮盘模式下分数为75％</p>
        </div>
        <div class="column">
          <h3 class="subtitle">
            <b-icon icon="shuffle-variant" />轮盘模式
          </h3>
          <p>此模式提供了额外的难度，并且具有更大的基本分数。</p>
          <p>抓到一些抓到的小精灵之后，将会重新洗牌。</p>
        </div>
      </div>

      <hr />
      <h2 class="title">得分</h2>
      <p>每个你抓到的宝可梦将会增加你的最终得分。这取决于选择的级别和模式。</p>
      <p>每次失败将会在得分上减少10%,最多减少90%</p>
      <table class="table is-bordered is-fullwidth">
        <thead>
          <tr>
            <th>难度</th>
            <th>基础模式 / 简单</th>
            <th>轮盘模式 / 简单</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="row in levelsList" :key="row.level">
            <td>{{ row.level }}</td>
            <td>{{ row.base | number }} / {{ row.base_easy | number }}</td>
            <td>{{ row.roulette | number }} / {{ row.roulette_easy | number }}</td>
          </tr>
        </tbody>
      </table>
    </section>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import { map } from 'lodash-es'

export default {
  name: 'InformationsModal',
  computed: {
    ...mapGetters(['levels']),
    levelsList() {
      return map(this.levels, level => {
        const base = Math.pow(level, 2)
        const roulette = Math.pow(level, 3)
        return {
          level: level * 2,
          base,
          roulette,
          base_easy: base * 0.5,
          roulette_easy: roulette * 0.25
        }
      })
    }
  }
}
</script>

<style lang="css" scoped>
</style>
