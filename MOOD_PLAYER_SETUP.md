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

**BELANGRIJK:** Deze app gebruikt JOUW echte muziek DNA, niet generieke profielen!

### 🎧 SPOTIFY DNA (Thuis/Onderweg)
Voor solo listening, headphones, thuis muziek luisteren:

- **Melodic Techno** (35% van je DNA)
  - Stephan Bodzin, Mind Against, Adriatique, Kevin de Vries
  - 122-128 BPM, melodisch & emotioneel

- **Tech House** (30% van je DNA)
  - CamelPhat, Hannah Wants, John Summit
  - Groovy & driving beats

- **Progressive Trance** (25% van je DNA)
  - Armin van Buuren, Above & Beyond, Cosmic Gate
  - Emotioneel & uplifting

- **Afro/World Influences** (10% van je DNA)
  - Black Coffee, Brazilian funk
  - Vakantie vibes

- **Mixed Spotify DNA**
  - Combinatie van alle Spotify stijlen

### 🎪 FESTIVAL DNA (Live/Dancefloor)
Voor festivals, clubs, dancefloor:

- **Hard/Industrial Techno**
  - Helena Hauff, Bassiani, Spekki Webu
  - THE TUNNEL vibes, 135-145 BPM, dark & relentless

- **Straightforward Dancefloor**
  - Job Jobse style
  - Pure techno, no-nonsense, 130-138 BPM

- **Classic House**
  - Benny Rodrigues b2b Carista style
  - Early house sound, 120-128 BPM

- **Peak Time Techno**
  - 999999999, I Hate Models, Freddy K, Kobosil
  - Late night energy, 138-145 BPM

### Het Verschil: Waarom twee profielen?

**Spotify DNA** = Solo listening, emotioneel, melodisch, 122-128 BPM
**Festival DNA** = Collective experience, pure energy, harder, 130-140+ BPM

Dit is normaal! Thuis luister je Miles Davis, op feestjes wil je hard techno.

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

## Adding Your Own DNA Profiles

Je kunt nieuwe DNA profielen toevoegen! Volg deze stappen:

### Stap 1: Open mood-player.html

### Stap 2: Voeg optie toe aan dropdown (regel ~318-332)

```html
<optgroup label="🎵 JOUW NIEUWE CATEGORIE">
    <option value="jouw_profiel_id">Jouw Profiel Naam</option>
</optgroup>
```

### Stap 3: Voeg profiel toe aan DNA_PROFILES (regel ~362-494)

```javascript
jouw_profiel_id: {
    name: 'Jouw Profiel Naam',
    description: 'Beschrijving van je profiel',
    features: {
        target_tempo: 125,        // BPM
        min_tempo: 120,
        max_tempo: 130,
        target_energy: 0.7,       // 0.0-1.0
        target_valence: 0.6,      // 0.0-1.0 (positivity)
        target_danceability: 0.75,
        target_instrumentalness: 0.4  // hoger = minder vocals
    },
    genres: ['genre1', 'genre2', 'genre3']  // optioneel
}
```

### Audio Features Guide:

- **tempo**: BPM (beats per minute)
- **energy**: 0.0-1.0 (intensity & activity)
- **valence**: 0.0-1.0 (musical positivity, higher = happier)
- **danceability**: 0.0-1.0 (how suitable for dancing)
- **instrumentalness**: 0.0-1.0 (hoger = meer instrumental, minder vocals)
- **acousticness**: 0.0-1.0 (acoustic vs electronic)
- **speechiness**: 0.0-1.0 (presence of spoken words)

### Spotify Genres:

Gebruik genres zoals: `techno`, `house`, `trance`, `hard-techno`, `melodic-techno`,
`tech-house`, `progressive-house`, `afro-house`, `deep-house`, `disco`, etc.

## Future Enhancements

Possible additions:
- Save generated playlists to your Spotify account
- Integration with Spotify Web Playback SDK for in-app playing
- Mood history tracking
- Share playlists with friends
- Import DNA profiles from external files

Enjoy your personalized mood music experience!
