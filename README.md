# Pokédex

A desktop Pokédex built with Python and Tkinter. Search for a Pokémon by name to see its artwork, type, stats and generation, then open charts that visualise its stats.

## Features

- **Search by name**: partial, case-insensitive matching (e.g. `char` returns the first Pokémon whose name contains "char").
- **Pokémon profile**: official artwork, name, primary type (colour-coded), a legendary badge, HP / Attack / Defense / Speed, total stats and generation.
- **Four chart types** in their own windows, coloured by the Pokémon's primary type:
  - Bar chart
  - Line graph
  - Horizontal bar chart
  - Radar chart
- **Animated loading screen** with a spinning Poké Ball while a search runs.
- **Image caching**: artwork is downloaded from [PokéAPI](https://pokeapi.co/) the first time and saved to `images/`, so later lookups load instantly and work offline.
- **Navy theme** throughout the interface.

## Project structure

```
Data-Programming/
├── Pokedex(main).py      # The application
├── Assets/
│   ├── Pokedex.png       # Logo shown at the top of the window
│   ├── pokeball.gif      # Loading animation
│   └── pokemon_data.csv  # Dataset (800 rows)
└── images/               # Cached Pokémon artwork (created automatically)
```

## Requirements

- Python 3.9 or newer
- Tkinter (included with most Python installs; on some Linux distros install `python3-tk`)
- The following packages:

```
pandas
numpy
matplotlib
Pillow
requests
```

## Installation and usage

1. Clone the repository:

   ```bash
   git clone https://github.com/Michal-Rogalewicz/Data-Programming.git
   cd Data-Programming
   ```

2. Install the dependencies:

   ```bash
   pip install pandas numpy matplotlib Pillow requests
   ```

3. Run the app **from the project folder**. It loads its files using relative paths:

   ```bash
   python "Pokedex(main).py"
   ```

4. Type a Pokémon name, press **Enter** or click **Search**, then use the buttons on the right to open a chart.

An internet connection is only needed the first time you look up a Pokémon whose artwork isn't already in `images/`. If the image can't be fetched, the app shows "Image not available" and carries on.

## Dataset

`Assets/pokemon_data.csv` has one row per Pokémon (including Mega forms) with these columns:

`#`, `Name`, `Type 1`, `Type 2`, `HP`, `Attack`, `Defense`, `Sp. Atk`, `Sp. Def`, `Speed`, `Generation`, `Legendary`

The interface currently displays HP, Attack, Defense and Speed.

## How it works

1. The CSV is loaded into a pandas DataFrame at startup.
2. A search filters the `Name` column for the text you typed and takes the first match.
3. The app looks for cached artwork in `images/`. If it isn't there, it queries PokéAPI for the official artwork and saves it.
4. The profile panel is updated, and each chart button builds a matplotlib figure embedded in a Tkinter window.

## Possible improvements

- Show Type 2, Sp. Atk and Sp. Def
- Let the user pick between several matches instead of always using the first
- Compare two Pokémon on one chart

## Credits

- Artwork and sprite data from [PokéAPI](https://pokeapi.co/)
- Pokémon is a trademark of Nintendo, Game Freak and Creatures Inc. This is a student project and is not affiliated with or endorsed by them.
