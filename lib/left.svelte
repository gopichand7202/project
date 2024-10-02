<!-- src/LeftSide.svelte -->
<script>
  // You can add any necessary logic here
</script>

<style>
  .left-side { 
      flex: 3; /* Takes 3 parts of the flex container, equivalent to 75% */
      height: 100vh;
      background-color: #f4f4f4; /* Light gray background */
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      box-sizing: border-box;
  }
  
  h1 {
      font-size: 2rem;
  }
  
  p {
      font-size: 1.2rem;
  }

  @media (max-width: 768px) {
      .left-side {
          padding: 10px;
           /* h1{
              font-size: 1.5rem;
          } 
          /* .p { */
              /* font-size: 1rem;
          } */ 
      }
  }
</style>

<div class="left-side">
  <h1>Left Side Content</h1>
  <p>This section covers 75% of the width.</p>
</div>
