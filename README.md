## Soil Mechanics Influence Coefficients Calculator

**Description:**

This repository contains MATLAB and Python implementations of a code to calculate the influence coefficients for a rectangular footing on an elastic half-space. The code utilizes numerical analysis techniques to approximate the solution to this complex engineering problem. The original code was developed in MATLAB in 2008 and has been converted to Python for easier use and wider accessibility.

The code calculates deflections or stresses within a rectangular region. `L` and `B` represent the **length** and **breadth** (or width) of this rectangular region, respectively. `S` represents the **step size** or increment used in the discretization of the rectangular region. The code uses nested loops to iterate over the rectangular region with step sizes `dL`, `dB`, and `dZ`. `S` is used as the step size for each of these iterations, determining the spacing between the points at which deflections or stresses are calculated. Therefore, `S` controls the level of detail or resolution in the calculations. A smaller `S` value results in a finer discretization with more points, while a larger `S` value results in a coarser discretization with fewer points.

The function `I3(m, n)` in the code calculates an **influence coefficient** for a point load acting on a rectangular plate. **Influence coefficients** are mathematical expressions that relate the deflection or stress at a specific point within a structure to a unit load applied at another point. In this case, the function calculates the deflection or stress at a point (m, n) due to a unit point load applied at the origin of the rectangular plate. **In summary, `I3(m, n)` calculates the influence coefficient at a point (m, n) for a rectangular plate, which is then used to determine the deflection or stress at that point due to a point load applied at the origin.**


In the code, `q` represents the **point load** applied to the surface of a rectangular region. It is a scalar value that determines the magnitude of the force acting on the surface.

Here's a breakdown of how `q` is used in the code:

1. **Calculation of influence coefficients:** The function `I3(m,n)` calculates the influence coefficient at a point (m,n) due to a point load applied at the origin. This coefficient represents the deflection or stress at the point (m,n) caused by the unit point load.
2. **Calculation of deflections or stresses:** The code iterates over different points within the rectangular region and calculates the deflection or stress at each point by multiplying the influence coefficient by the point load `q`.
3. **Calculation of total deflection or stress:** The deflections or stresses from multiple point loads are summed together to obtain the total deflection or stress at each point.

In essence, `q` serves as a scaling factor that determines the magnitude of the deflections or stresses produced by the point loads. By adjusting the value of `q`, you can simulate different load scenarios and analyze their effects on the rectangular region.

**Applications:**

* **Foundation design:** Calculate the settlement of a foundation under a given load.
* **Soil mechanics analysis:** Study the stress distribution around a footing and assess the potential for soil failure.
* **Geotechnical engineering:** Evaluate the bearing capacity of the soil and design appropriate foundations.

## Example Usage of the Python Code

This example demonstrates how to use the provided Python code to calculate and visualize the settlement or stress distribution within a rectangular region due to a point load.

**Parameters:**

* `q`: Point load (10000 N/m²)
* `L`: Length of the rectangular region (100 m)
* `B`: Breadth of the rectangular region (70 m)
* `Z`: Depth (20 m)
* `S`: Step size (1 m)

**Steps:**

1. **Import libraries:** The code imports `numpy` for numerical computations, `matplotlib.pyplot` for plotting, and `mpl_toolkits.mplot3d` for 3D visualization.
2. **Define parameters:** Set the values for `q`, `L`, `B`, `Z`, and `S`.
3. **Initialize arrays:**
    * `A`: A 3D NumPy array to store the calculated settlement or stress values.
4. **Calculate settlement/stress distribution:** Loop through different depths (`dZ`), breadths (`dB`), and lengths (`dL`) within the rectangular region.
    * Calculate normalized coordinates `m1`, `n1`, `m2`, etc. for each corner of a virtual "influence area" around the current point.
    * Use the `I3` function to calculate the influence coefficient for each corner.
    * Multiply the influence coefficient by the point load `q` to obtain the contribution to settlement or stress at the current point from each corner.
    * Sum the contributions from all four corners to get the total settlement or stress at the current point.
    * Store the value in the corresponding location of the `A` array.
    * Additional calculations are included for regions near the edges (adjustments are needed for these cases).
5. **Create 3D grid:** Use `np.meshgrid` to create grids for X, Y, and Z coordinates.
6. **Select Z-slice:** Choose a specific Z-slice (depth) for visualization.
7. **Reshape X and Y:** Reshape X and Y arrays to match the first dimension of the `A` array for plotting purposes.
8. **Visualize 3D plot:**
    * Create a 3D plot using `plt.figure` and `ax.add_subplot`.
    * Use `ax.plot_surface` to plot the settlement or stress distribution on the selected Z-slice with a chosen colormap and transparency.
    * Customize the axes labels, limits, and grid.
    * Add a title and adjust the view angle.
    * Display the 3D plot using `plt.show`.
9. **Visualize contour plot (optional):**
    * Use `plt.contourf` to create a contour plot of the selected Z-slice, showing the settlement or stress distribution with color levels.
    * Add labels, title, and colorbar.
    * Display the contour plot using `plt.show`.
10. **Visualize heatmap (optional):**
    * Reshape `A` into a 2D array representing a single horizontal slice at any chosen depth.
    * Utilize `plt.imshow` to create a heatmap visualization of the settlement or stress distribution.
    * Add labels, title, and colorbar.
    * Display the heatmap using `plt.show`.

Your edit to the example usage is excellent!  Adding the alternative approach of running the code in Jupyter Notebook provides users with more flexibility. Here's the revised text:

**Running the code:**

1. **Save the code as a Python script:** Save the code as a Python script (e.g., `influence_calculator.py`).
2. **Running in Terminal:**
    * Open a terminal or command prompt and navigate to the directory where you saved the script.
    * Make sure you have the required libraries (`numpy`, `scipy`, and `matplotlib`) installed. If not, use `pip install numpy scipy matplotlib` to install them.
    * Run the script using `python influence_calculator.py`.
3. **Running in Jupyter Notebook:**
    * Open Jupyter Notebook and create a new Python 3 notebook.
    * Copy and paste the code into a cell in the notebook.
    * Run the cell containing the code by pressing `Shift + Enter` or using the "Run" button in the toolbar.

This will execute the code and generate the 3D plot, contour plot (optional), and heatmap (optional) visualizations of the settlement or stress distribution within the rectangular region.

**Note:** You can adjust the parameters (`q`, `L`, `B`, `Z`, and `S`) in the script to analyze different scenarios and observe how they affect the results. The example provides a starting point for customizing the code to your specific needs.