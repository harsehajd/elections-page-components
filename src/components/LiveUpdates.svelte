<script>
	import { onMount } from 'svelte';
  
	let updates = [
	  { type: "winner", author: "Lee Davidson", time: "2 minutes ago", content: "Claudia Tenney (Republican) wins New York's 22nd Congressional District." },
	  { author: "Lee Davidson", time: "4 minutes ago", content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat." },
	  { author: "Lee Davidson", time: "7 minutes ago", content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat." },
	  // ... (other updates)
	];
  
	let windowHeight;
  
	onMount(() => {
	  const updateWindowHeight = () => {
		windowHeight = window.innerHeight;
	  };
	  
	  updateWindowHeight();
	  window.addEventListener('resize', updateWindowHeight);
  
	  return () => {
		window.removeEventListener('resize', updateWindowHeight);
	  };
	});
  </script>
  
  <div class="live-updates-container">
	<div class="live-updates" style="max-height: {windowHeight - 40}px">
	  <h2>Live updates</h2>
	  <div class="updates-scroll">
		{#each updates as update}
		  <div class="update" class:winner={update.type === "winner"}>
				{#if update.type === "winner"}
				  <div class="winner-label">WINNER</div>
				  <div class="winner-icon">›</div>
				{/if}
				<div class="update-header">
				  <span class="author">{update.author}</span>
				  <span class="time">{update.time}</span>
					</div>
				<p class="content">{update.content}</p>
		  </div>
		{/each}
	  </div>
	</div>
  </div>
  
  <style>
	@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

	.live-updates-container {
	  position: fixed;
	  top: 20px;
	  right: 20px;
	  width: 300px;
	  z-index: 10;
	  font-family: 'Roboto', Arial, sans-serif;
	}
  
	.live-updates {
	  background-color: #ffffff;
	  border: 1px solid #e2e2e2;
	  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
	  overflow-y: auto;
	}
  
	h2 {
	  font-size: 1.1rem;
	  font-weight: 700;
	  margin: 0;
	  color: #1a1a1a;
	  position: sticky;
	  top: 0;
	  background-color: #ffffff;
	  padding: 15px;
	  border-bottom: 1px solid #e2e2e2;
	}
  
	.updates-scroll {
	  overflow-y: auto;
	  max-height: calc(100% - 60px);
	}
  
	.update {
	  padding: 15px;
	  border-bottom: 1px solid #e2e2e2;
	  position: relative;
	}
  
	.update:last-child {
	  border-bottom: none;
	}
  
	.update-header {
	  margin-bottom: 5px;
	}
  
	.author {
	  font-weight: bold;
	  font-size: 0.9rem;
	  color: #1a1a1a;
	}
  
	.time {
	  color: #666;
	  font-size: 0.8rem;
	  margin-left: 10px;
	}
  
	.content {
	  margin: 0;
	  font-size: 0.9rem;
	  line-height: 1.4;
	  color: #333;
	}
  
	.update.winner {
	  background-color: #f8f8f8;
	  border-left: 4px solid #d0021b;
	  padding-left: 11px;
	}
  
	.winner-label {
	  font-size: 0.75rem;
	  font-weight: bold;
	  color: #d0021b;
	  margin-bottom: 5px;
	}
  
	.winner-icon {
	  position: absolute;
	  top: 15px;
	  right: 15px;
	  font-size: 1.2rem;
	  color: #d0021b;
	  font-weight: bold;
	}
  </style>
