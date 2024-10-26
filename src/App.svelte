<script>
	import ResultsTable from './components/ResultsTable.svelte';
	import LiveUpdates from './components/LiveUpdates.svelte';
  
	const candidatesData = [
	  {
		name: 'Mark Robinson',
		party: 'Republican',
		partyColor: '#bf1d29',
		votes: 574208,
		percentage: 49.9,
		imageUrl: 'mark-robinson-image.jpg'
	  },
	  {
		name: 'Josh Stein',
		party: 'Democrat',
		partyColor: '#3c8aca',
		votes: 576932,
		percentage: 50.1,
		imageUrl: 'josh-stein-image.jpg'
	  }
	];
  </script>
  
  <div class="election-results-container">
	<div class="main-content">
	  <h1>Gubernatorial Election Results</h1>
	  <p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut
	  laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation
	  ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.</p>
	  <ResultsTable candidates={candidatesData} />
	  <!-- Add other components here -->
	</div>
	<div class="sidebar">
	  <LiveUpdates />
	</div>
  </div>
  
  <style>
	.election-results-container {
	  display: flex;
	  gap: 40px; /* Increased gap between main content and sidebar */
	  max-width: 1200px; /* Adjust as needed */
	  margin: 0 auto;
	  padding: 0 20px; /* Add some horizontal padding */
	}
	.main-content {
	  flex: 1;
	  padding-left: 20px; /* Add left padding to main content */
	}
	.sidebar {
	  width: 300px; /* Adjust as needed */
	}
	h1 {
	  font-size: 36px;
	  margin-bottom: 20px;
	}
	p {
	  font-size: 16px;
	  line-height: 1.5;
	  margin-bottom: 30px; /* Add more space before the results table */
	}
  </style>