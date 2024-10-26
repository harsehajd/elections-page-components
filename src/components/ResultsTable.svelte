<script>
  export let candidates = [];
</script>

<div class="results-table">
  <table>
    <thead>
      <tr>
        <th>Candidate</th>
        <th>Party</th>
        <th>Votes</th>
        <th>Pct.</th>
      </tr>
    </thead>
    <tbody>
      {#each candidates as candidate}
        <tr>
          <td class="candidate">
            <div class="party-indicator" style="background-color: {candidate.partyColor};"></div>
            <img src={candidate.imageUrl} alt={candidate.name} class="candidate-image" />
            <span>{candidate.name}</span>
          </td>
          <td>{candidate.party}</td>
          <td>{candidate.votes.toLocaleString()}</td>
          <td>{candidate.percentage}%</td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
  .results-table {
    width: 100%;
    font-family: Arial, sans-serif;
    margin-bottom: 20px;
  }

  table {
    width: 100%;
    border-collapse: collapse;
  }

  th, td {
    padding: 10px 5px;
    text-align: left;
    border-bottom: 1px solid #e2e2e2;
  }

  th {
    font-weight: normal;
    font-size: 14px;
    color: #666;
  }

  td {
    font-size: 16px;
  }

  .candidate {
    display: flex;
    align-items: center;
  }

  .party-indicator {
    width: 4px;
    height: 30px;
    margin-right: 10px;
  }

  .candidate-image {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin-right: 10px;
  }
</style>
