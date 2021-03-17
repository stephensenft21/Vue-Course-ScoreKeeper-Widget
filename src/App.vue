<template>
  <div id="app">
 <matchup-header :teams="teams" />
    <results-container :teams="teams" />
    
  </div>
</template>

<script>
import MatchupHeader from './components/MatchupHeader.vue'

export default {
  name: '',
  components: {
    MatchupHeader
 
  },
    data() {
      return {

  teams: [
        {
          name: "Team 1",
          score: 0,
          winning: false
        },
        {
          name: "Team 2",
          score: 0,
          winning: false
        }
      ]
      }

    },
    methods: {
    checkWinner() {
      const [team1, team2] = this.teams;
      if (team1.score > team2.score) {
        team1.winning = true;
        team2.winning = false;
      } else if (team1.score < team2.score) {
        team1.winning = false;
        team2.winning = true;
      } else if (team1.score === team2.score) {
        team1.winning = false;
        team2.winning = false;
      }
    },
    handleAddScore(team) {
      ++team.score;
      this.checkWinner();
    },
    handleRemoveScore(team) {
      team.score !== 0 && --team.score;
      this.checkWinner();
    }
  },

}
</script>

<style>
#app {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  font-family: sans-serif;
  color: rgb(41, 41, 41);
  background-color: var(--background);
  box-sizing: content-box;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}
</style>
