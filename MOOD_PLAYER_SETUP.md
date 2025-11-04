# Mood Music Player - Setup Guide

Your mood-based music player is ready! Here's how to set it up and start using it.

## What You Get

- **6 Mood Options**: Happy, Sad, Energetic, Chill, Focused, Romantic
- **8 Music DNA Profiles**: Dance Party, Acoustic Vibes, Electronic Focus, Vocal Power, Upbeat Pop, Indie Alternative, Hip Hop & R&B, Rock Energy
- **Smart Recommendations**: Uses Spotify's audio features (valence, energy, danceability, etc.) to find perfect tracks
- **Mobile & Desktop**: Fully responsive design works on your phone and MacBook

## Setup Instructions

### Step 1: Create a Spotify App

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Log in with your Spotify account
3. Click **"Create app"**
4. Fill in the details:
   - **App name**: Mood Music Player (or whatever you like)
   - **App description**: Personal mood-based music player
   - **Redirect URI**: `https://YOURUSERNAME.github.io/mood-player.html` (replace YOURUSERNAME with your actual GitHub username)
   - **API/SDKs**: Check "Web API"
5. Accept the terms and click **"Save"**
6. You'll see your **Client ID** - copy this!

### Step 2: Configure Your App

1. Open the file `mood-player.html` in a text editor
2. Find this line (around line 328):
   ```javascript
   const CLIENT_ID = 'YOUR_SPOTIFY_CLIENT_ID';
   ```
3. Replace `YOUR_SPOTIFY_CLIENT_ID` with your actual Client ID from Step 1
4. Save the file

### Step 3: Deploy to GitHub Pages

1. Commit and push the changes:
   ```bash
   git add mood-player.html
   git commit -m "Add mood-based music player"
   git push
   ```

2. Make sure GitHub Pages is enabled for your repository:
   - Go to your repository settings
   - Scroll to "Pages"
   - Ensure "Source" is set to deploy from your main branch

### Step 4: Access Your Player

Open your browser and go to:
```
https://YOURUSERNAME.github.io/mood-player.html
```

Replace `YOURUSERNAME` with your GitHub username.

## How to Use

1. **Connect Spotify**: Click "Connect Spotify" and authorize the app
2. **Select Your Mood**: Tap one of the 6 mood options
3. **Choose Music DNA**: Select which style of music you want
4. **Generate Playlist**: Click the button to get personalized recommendations
5. **Play Music**: Click "Play" on any track to open it in Spotify

## Music DNA Profiles Explained

- **Dance Party**: High energy, highly danceable tracks
- **Acoustic Vibes**: Unplugged, organic acoustic sounds
- **Electronic Focus**: Instrumental electronic beats for concentration
- **Vocal Power**: Strong vocals and lyrical content
- **Upbeat Pop**: Catchy, feel-good pop music
- **Indie Alternative**: Alternative and indie rock vibes
- **Hip Hop & R&B**: Urban beats and smooth R&B
- **Rock Energy**: High energy rock tracks

## How the Mood Mapping Works

The app uses Spotify's audio features to match your mood:

- **Happy**: High valence (positivity), high energy
- **Sad**: Low valence, low energy, minor mode
- **Energetic**: Very high energy and danceability
- **Chill**: Low energy, high acousticness
- **Focused**: Balanced energy, higher instrumentalness
- **Romantic**: Moderate valence, lower energy, acoustic elements

## Troubleshooting

### "Error: 401 Unauthorized"
Your access token expired. Refresh the page and log in again.

### "No tracks found"
Try a different combination of mood and DNA. Some combinations might have limited results depending on your listening history.

### "API Error: 403"
Make sure:
1. Your Client ID is correct
2. The Redirect URI in your Spotify app matches exactly
3. You've added the correct redirect URI in the Spotify Developer Dashboard

### Not finding music you like?
The app uses your recent listening history as "seeds" for recommendations. The more you use Spotify normally, the better the recommendations will be!

## Mobile Access

The app is fully mobile-responsive! Simply open the URL on your phone's browser:
```
https://YOURUSERNAME.github.io/mood-player.html
```

You can also:
- Add it to your home screen on iPhone (Share → Add to Home Screen)
- Add it to your home screen on Android (Menu → Add to Home Screen)

This gives you a quick-launch icon like a native app!

## Technical Details

- **Authentication**: Uses OAuth 2.0 with PKCE (Proof Key for Code Exchange)
- **Audio Features**: Leverages Spotify's track analysis including valence, energy, danceability, acousticness, instrumentalness, and more
- **Recommendations API**: Combines your listening history with target audio features
- **Storage**: Access token stored in browser's localStorage for convenience

## Privacy

- Your Spotify credentials are never stored
- Only you can see your music and preferences
- The app runs entirely in your browser
- No data is sent to any third-party servers

## Future Enhancements

Possible additions:
- Save generated playlists to your Spotify account
- Create custom Music DNA profiles
- Integration with Spotify Web Playback SDK for in-app playing
- Mood history tracking
- Share playlists with friends

Enjoy your personalized mood music experience!
