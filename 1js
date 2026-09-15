// Function to clear the Watch Later playlist automatically
(async function clearWatchLater() {
  // Find all three-dot action menu buttons for the videos listed on the page
  const menuButtons = document.querySelectorAll('ytd-playlist-video-renderer #button.ytd-menu-renderer');

  // If no menu buttons are found, there are no more visible videos to process
  if (menuButtons.length === 0) {
    console.log("No more videos found or playlist is empty.");
    return;
  }

  // Iterate over each video's menu button sequentially
  for (let i = 0; i < menuButtons.length; i++) {
    // Step 1: Click the three-dot menu button to open the dropdown options
    menuButtons[i].click();
    
    // Pause briefly (500ms) to allow the menu popup to render in the DOM
    await new Promise(resolve => setTimeout(resolve, 500));

    // Step 2: Search for the "Remove from Watch later" menu option item
    const menuItems = document.querySelectorAll('ytd-menu-service-item-renderer');
    let removeButton = null;

    // Search through menu items to find the one matching the removal text
    menuItems.forEach(item => {
      if (item.innerText.includes("Remove from")) {
        removeButton = item;
      }
    });

    // Step 3: Click the remove option if it was successfully located
    if (removeButton) {
      removeButton.click();
      console.log(`Removed video ${i + 1} of ${menuButtons.length}`);
    }

    // Pause briefly (1000ms) before moving to the next video to avoid triggering rate limits
    await new Promise(resolve => setTimeout(resolve, 1000));
  }

  console.log("Finished processing current visible batch. Scroll down or refresh if more videos remain.");
})();