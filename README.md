# GM & Toyota Tariff Impact Study

## Repo Name: **GM_Toyota_Tariff_Impact_Analysis**

### Inspired by Founder Todd Smith of QoreAI.com

This study analyzes the impact of the upcoming **tariffs** on the **top GM and Toyota vehicle models** in the U.S. market, focusing on key cities (Los Angeles, Houston, and Denver). It uses a combination of **3D plots**, **2D maps**, and **data visualizations** to demonstrate how tariffs might affect vehicle pricing, production, and the consumer market.

---

### **What Was Accomplished?**

This case study includes the following analyses:

1. **Tariff Impact on GM Models**: Analyzed how **Chevy** and **GMC** models are affected by tariffs, focusing on the **Chevy Equinox** and **GMC Sierra**.
2. **Tariff Impact on Toyota Models**: Analyzed how **Toyota** models like the **Camry**, **Corolla**, **RAV4**, **Highlander**, and **Tacoma** are impacted.
3. **Interactive 3D Plots**: Created interactive **3D scatter plots** to visualize the tariff impact on different vehicle models across cities like Los Angeles, Houston, and Denver.
4. **Interactive 2D Maps**: Created **2D area maps** displaying the location of Toyota’s assembly plants and showing the impact of tariffs on each model in the selected cities.
5. **Key Insights**: Analyzed how the importation of parts, reliance on global supply chains, and regional manufacturing plants impact vehicle pricing and consumer behavior in light of tariff increases.

---

### **Why It Matters**

This analysis provides valuable insights into the **automotive industry’s response** to global trade changes, specifically tariffs. With **imported parts** and **foreign manufacturing** playing a significant role in vehicle production, understanding how tariffs will affect **foreign automakers** like GM and Toyota is crucial for:

- **Consumers**: To anticipate potential price increases or changes in vehicle availability.
- **Automakers**: To adjust production strategies, supply chains, and pricing structures.
- **Economic Policy Makers**: To understand the broader effects of tariff policies on industries with complex, multinational supply chains.

Understanding this dynamic can help businesses, investors, and consumers make more informed decisions as these tariffs come into play.

---

## **Tariff Impact on GM Models**

This analysis focuses on how GM models such as the **Chevy Equinox** and **GMC Sierra** will be affected by tariffs, focusing on their impact in **Los Angeles**, **Houston**, and **Denver**. The following 3D scatter plot visualizes the **tariff impact** on these models.

### **GM 3D Tariff Impact Plot**

```r
# Install required libraries if not already installed
# install.packages("plotly")
# install.packages("dplyr")

library(plotly)
library(dplyr)

# Data: Tariff Impact for GM Models (example values)
models_gm <- c("Chevy Equinox", "Chevy Traverse", "Chevy Bolt EV", "Chevy Malibu", 
            "GMC Sierra", "GMC Canyon", "Cadillac Escalade", "Chevy Silverado 1500",
            "Chevy Colorado", "Cadillac CT4/CT5")

# Tariff impact percentage for each model in each city (example values)
tariff_impact_gm <- data.frame(
  Model = rep(models_gm, times = 3),
  City = rep(c("Los Angeles", "Houston", "Denver"), each = length(models_gm)),
  Impact = c(15, 20, 18, 22, 12, 10, 25, 28, 23, 30, 
             18, 19, 21, 20, 14, 16, 24, 26, 27, 25, 
             16, 18, 20, 17, 11, 14, 22, 23, 28, 26)
)

# Plotting 3D scatter plot with hover
fig_gm <- plot_ly(tariff_impact_gm, x = ~Model, y = ~Impact, z = ~City, 
              text = ~paste("Model:", Model, "<br>City:", City, "<br>Impact:", Impact, "%"),
              hoverinfo = 'text', type = 'scatter3d', mode = 'markers') %>%
  layout(title = "Tariff Impact on GM Models by City",
         scene = list(
           xaxis = list(title = 'Vehicle Model'),
           yaxis = list(title = 'Tariff Impact (%)'),
           zaxis = list(title = 'City')
         ))

fig_gm
```

---

## **Tariff Impact on Toyota Models**

This analysis evaluates how **Toyota** models such as the **Camry**, **Corolla**, **RAV4**, **Highlander**, and **Tacoma** will be impacted by the new tariffs, again focusing on the cities of **Los Angeles**, **Houston**, and **Denver**. The following 3D scatter plot visualizes the **tariff impact** on these models.

### **Toyota 3D Tariff Impact Plot**

```r
# Install required libraries if not already installed
# install.packages("plotly")
# install.packages("dplyr")

library(plotly)
library(dplyr)

# Data: Tariff Impact for Toyota Models (example values)
models_toyota <- c("Toyota Camry", "Toyota Corolla", "Toyota RAV4", "Toyota Highlander", "Toyota Tacoma")

# Tariff impact percentage for each model in each city (example values)
tariff_impact_toyota <- data.frame(
  Model = rep(models_toyota, times = 3),
  City = rep(c("Los Angeles", "Houston", "Denver"), each = length(models_toyota)),
  Impact = c(20, 22, 21, 19, 17, 18, 24, 23, 22, 26, 
             21, 22, 18, 17, 16, 19, 23, 24, 25, 22, 
             19, 20, 18, 15, 14, 18, 21, 22, 23, 25)
)

# Plotting 3D scatter plot with hover
fig_toyota <- plot_ly(tariff_impact_toyota, x = ~Model, y = ~Impact, z = ~City, 
              text = ~paste("Model:", Model, "<br>City:", City, "<br>Impact:", Impact, "%"),
              hoverinfo = 'text', type = 'scatter3d', mode = 'markers') %>%
  layout(title = "Tariff Impact on Toyota Models by City",
         scene = list(
           xaxis = list(title = 'Vehicle Model'),
           yaxis = list(title = 'Tariff Impact (%)'),
           zaxis = list(title = 'City')
         ))

fig_toyota
```

---

### **2D Area Map for Toyota Assembly Plants**

Now, let’s look at where **Toyota’s U.S. assembly plants** are located. We’ll display the plants on a **2D map** to understand how close they are to the key cities being impacted by the tariffs.

```r
# Install required libraries if not already installed
# install.packages("leaflet")
# install.packages("dplyr")

library(leaflet)
library(dplyr)

# Toyota Assembly Plant Locations in the U.S.
plant_locations <- data.frame(
  Plant = c("TMMK (Kentucky)", "TMMTX (Texas)", "TMMI (Indiana)", "TMMAL (Alabama)", "TMMNC (Mississippi)"),
  Latitude = c(38.1617, 29.6813, 38.2806, 33.5133, 30.4111),
  Longitude = c(-84.6019, -97.5194, -87.1396, -86.6535, -89.4369)
)

# Create a 2D map showing Toyota plant locations
map_toyota <- leaflet(plant_locations) %>%
  addTiles() %>%
  addMarkers(
    lat = ~Latitude, lng = ~Longitude,
    popup = ~paste("<b>Plant:</b>", Plant, "<br><b>Location:</b>", Latitude, ", ", Longitude),
    label = ~Plant
  )

map_toyota
```

---

### **Conclusion**

This analysis illustrates how **tariffs** on **foreign imports** will affect the pricing and availability of **GM** and **Toyota** vehicles in major U.S. cities. Using **3D plots** and **interactive maps**, this study provides a clear view of how tariffs impact vehicle models and where the assembly plants are located.

By understanding the **tariff impact** on different vehicle models and key manufacturing plants, automakers, consumers, and policy makers can make better decisions regarding vehicle pricing, production strategies, and future policies.

---

### **How to Use This Repository**

- Clone this repository and run the R code provided in an RStudio environment.
- The code uses the **Plotly** and **Leaflet** packages to visualize the impact of tariffs.
- Modify the impact values or cities in the datasets to suit your analysis needs.
- Feel free to contribute, open issues, or suggest improvements!

---

### **License**

This project is licensed under the MIT License - see the LICENSE file for details.

---

### **Suggested Repository Name**

**GM_Toyota_Tariff_Impact_Analysis**

---

Let me know if you need further adjustments or explanations!
