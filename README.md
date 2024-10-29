
# Monte Carlo Stellar Evolution Simulation

### Author:
Mauricio Gracia  
Universidad Tecnica Federico Santa Maria  

### Description
This notebook performs a Monte Carlo simulation to model stellar evolution across a range of initial stellar masses and ages. The simulation calculates main sequence lifetimes and eventual remnant types (e.g., White Dwarfs, Neutron Stars, or Black Holes) based on a probabilistic initial mass function (IMF) and initial stellar conditions. The notebook also generates various visualizations, such as histograms and scatter plots, to represent the final distributions of star remnants and properties.

### Files
- **README.txt**: This documentation file.
- **simulation_*_stars.csv**: Output CSV files storing individual star properties for each specified simulation count.
- **initial_final_mass_scatter_all.png**: Plot showing initial vs. final mass distributions for each remnant type across all simulations.
- **age_histogram_all.png**: Histogram showing age distributions for various remnant types across all simulations.
- **mass_histogram_all.png**: Histogram showing final mass distributions for various remnant types across all simulations.

### Requirements
- **Python 3.12.4**
- **Libraries**: `numpy`, `pandas`, `matplotlib`, `glob`

### Notebook Workflow

1. **Setup and Imports**  
   Imports required libraries (`numpy`, `pandas`, `matplotlib`, `glob`) and initializes simulation parameters such as star counts, mass limits, and maximum age.

2. **Functions**  
   - `kroupa_imf(min_mass, max_mass)`: Generates an initial mass for a star based on the Kroupa Initial Mass Function (IMF).
   - `assign_birth_times(max_age)`: Assigns a uniform birth time for each star up to `max_age`.
   - `main_sequence_lifetime(mass, birth_time, max_age)`: Calculates the main sequence lifetime for a star.
   - `determine_stellar_remnant(initial_mass)`: Determines the type of stellar remnant based on initial mass and returns the remnant mass and type.
   - `get_norm_hist(Data_Frame, category, bins=100, density=False, log=True)`: Creates normalized histograms for specified categories across stellar remnants.
   - `make_star_life(min_mass, max_mass, max_age)`: Aggregates initial mass, birth time, main sequence lifetime, and remnant properties for each star, outputting these as a dictionary.

3. **Simulation Execution**  
   For each specified star count, the notebook:
   - Generates individual star data by simulating properties (mass, age, remnant type).
   - Stores results in a CSV file (e.g., `simulation_1000_stars.csv`).
   - Displays elapsed time for each simulation.

4. **Data Loading and Analysis**  
   Loads the generated CSV files, stores them in a dictionary, and processes the data to create normalized histograms and other summary statistics for final masses and ages.

5. **Visualization**  
   - **Histograms**: Plots normalized histograms for both `final_mass` and `t_born` (age at birth) for each remnant type across simulations.
   - **Scatter Plots**: Plots initial vs. final mass distributions, showing remnant types and their relationships to initial conditions.

6. **Fraction Analysis**  
   Calculates and displays the fraction of each remnant type (e.g., Main Sequence, White Dwarf) as part of the total star population for each simulation.

### Usage
1. **Run the Notebook**: Execute each cell sequentially. The notebook will automatically generate CSV files for each simulation, visualizations, and summary statistics.
2. **Interpret Results**: Review the generated plots and CSV files to understand the distribution of star remnants and their properties.

### Parameters
Key parameters in the simulation:
- `numbers_of_stars`: Array specifying the number of stars to simulate for each run (e.g., `[100, 1000, 10000]`).
- `min_mass`, `max_mass`: Define the range of initial stellar masses in solar masses.
- `max_star_age`: Maximum age for stars, typically representing the Milky Way's age (10 Gyr).

### Output
The simulation produces:
- CSV files containing individual star data for each simulation count.
- Plots showing distribution histograms for final mass and age, and scatter plots of initial vs. final mass for each star type.
