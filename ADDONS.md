# WayVibe Addon Hosting Guide

WayVibe uses a decentralized addon system inspired by Stremio. You can host your own addons on GitHub Pages for free.

## How to host your own Addon

1. **Create a GitHub Repository**: Create a new public repository (e.g., `wayvibe-my-addon`).
2. **Add a `manifest.json`**: Create a file named `manifest.json` in the root of your repository.
   ```json
   {
     "id": "community.my_addon",
     "name": "My Custom Source",
     "description": "Description of what this addon does",
     "version": "1.0.0",
     "resources": ["catalog", "stream"],
     "types": ["track"],
     "category": "community"
   }
   ```
3. **Enable GitHub Pages**:
   - Go to **Settings** -> **Pages**.
   - Under **Build and deployment**, select the `main` branch and `/root` folder.
   - Click **Save**.
4. **Install in WayVibe**:
   - Once your page is live (usually `https://username.github.io/repo-name/`), copy the URL.
   - In WayVibe, go to the **Addons** tab, click the **+** button, and paste the URL.

## Managing the Global Repository

The global list of addons is managed via a JSON file. By default, WayVibe looks at:
`https://raw.githubusercontent.com/WayVibe/addons/main/community_addons.json`

To host your own global list:
1. Copy the `community_addons.json` template from this project.
2. Host it on GitHub.
3. Update the `_defaultRepoUrl` in `lib/features/music/services/addon_manager.dart` to point to your new raw URL.
