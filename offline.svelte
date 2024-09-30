<script>
    let searchQuery = ''; // To hold the name of the selected file
    let selectedFile = null; // To store the selected file
    let showUploadPage = false; // Flag to toggle between search and upload display
  
    // Handle Browse button click (open file dialog)
    const handleBrowse = (event) => {
      const file = event.target.files[0];
      if (file) {
        searchQuery = file.name; // Set file name to search bar
        selectedFile = file;     // Store the file for uploading later
      }
    };
  
    // Handle Upload button click
    const handleUpload = () => {
      if (selectedFile) {
        showUploadPage = true; // Show the upload section
      }
    };
  
    // Function to reset to the search page
    // const resetToSearch = () => {
    //   searchQuery = '';
    //   selectedFile = null;
    //   showUploadPage = false; // Go back to search page
    // };
  </script>
  
  <style>
    .container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
  
    input[type="text"] {
      width: 300px;
      padding: 10px;
      font-size: 16px;
      border: 2px solid #ccc;
      border-radius: 5px;
      margin-bottom: 20px;
    }
  
    .buttons {
      display: flex;
      gap: 20px;
    }
  
    button {
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }
  
    button:hover {
      background-color: #0056b3;
    }
    
    .upload-section {
    display: flex; /* Flexbox for side-by-side layout */
    justify-content: space-between;
    align-items: flex-start; /* Align items at the top */
    margin-top: 20px; /* Space above the section */
    width: 100%; /* Full width */
    max-width: 800px; /* Limit maximum width */
  }
    .image-container {
    display: flex;
    flex-direction: column;
    align-items: center; /* Center the image and text */
    margin-top: 20px; /* Space above the image */
    padding: 20px; /* Space around the image */
    border: 1px solid #ccc; /* Optional: border around the image container */
    border-radius: 10px; /* Rounded corners */
    background-color: #f9f9f9; /* Light background color */
    max-width: 90%; /* Maximum width for the image container */
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Subtle shadow */
  }

    img {
      max-width: 100%;
      height: auto;
      border: 2px solid #ccc;
      border-radius: 5px;
      margin-top: 20px;
    }

    .form-container {
    display: flex;
    flex-direction: column;
    max-width: 45%; /* Maximum width for the form container */
    width: 100%; /* Full width */
  }

  </style>
  
  <!-- Page Content -->
  <div class="container">
    {#if showUploadPage}
      <!-- Upload Display Section -->
    <div class="upload-section">
        <!--Image display -->
      <div class="image-container">
      <!-- <h2>Uploaded Image: {selectedFile.name}</h2> -->
      <img src={URL.createObjectURL(selectedFile)} alt="Uploaded Image" />
      </div>
      <!-- Additional Form for Image Data -->
      <div class="form-container">
        <h3>Image Details</h3>
        <input 
          type="text" 
          
          placeholder="Enter additional data..." 
        />
      </div>
    </div>
      <!-- <button on:click={resetToSearch}>Back to Search</button> -->
    {:else}
      <!-- Search Section -->
      <input type="text" bind:value={searchQuery} placeholder="Browse a file..." readonly />
  
      <!-- Hidden file input for browsing -->
      <input type="file" accept="image/*" id="fileInput" style="display: none;" on:change={handleBrowse} />
  
      <!-- Buttons (Upload and Browse) -->
      <div class="buttons">
        <button on:click={() => document.getElementById('fileInput').click()}>Browse</button>
        <button on:click={handleUpload} disabled={!selectedFile}>Upload</button>
      </div>
    {/if}
  </div>
  