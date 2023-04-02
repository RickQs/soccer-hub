<template>
  <h1>Today Matches</h1>
  <ul>
    <li v-for="match, index in data.matches" :key="index">
      {{ match.homeTeam.shortName }} {{ match.score.fullTime.home }} X {{ match.score.fullTime.away }} {{ match.awayTeam.shortName }} ({{ match.status }})
    </li>
    <!-- <li>matches</li> -->
  </ul>
</template>

<script lang="ts">
export default defineComponent({
  async setup() {
    const { data }: { data: any } = await useFetch('https://api.football-data.org/v4/matches/',
      {
        method: 'GET',
        headers: { 'X-Auth-Token': 'c959da3284d94700b0c23cd1686b8f5b' }
      }
    )

    return { data }
  },
})
</script>