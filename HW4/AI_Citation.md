A.I. Citation for Homework #4:


# CREATING FIGURES TO DISPLAY HOW INDIVIDUAL VARIABLES RELATE TO EACH OTHER AND HOW THE CLASSES WITHIN THEM RELATE

# Taking another look at selected data, this time color-coded by wine class

plt.scatter(wine.data[:,1], wine.data[:,9], s = 30, c = wine.target) # c = wine.target is the part that does the color coding

plt.ylabel(wine.feature_names[9])

plt.xlabel(wine.feature_names[1])

plt.show()



# Taking another look at selected data, this time color-coded by wine class

plt.scatter(wine.data[:,5], wine.data[:,6], s = 30, c = wine.target) # c = wine.target is the part that does the color coding

plt.ylabel(wine.feature_names[6])

plt.xlabel(wine.feature_names[5])

plt.show()



# Taking another look at selected data, this time color-coded by wine class

plt.scatter(wine.data[:,0], wine.data[:,3], s = 30, c = wine.target) # c = wine.target is the part that does the color coding

plt.ylabel(wine.feature_names[3])

plt.xlabel(wine.feature_names[0])

plt.show()

This code snippet explores the classic Wine dataset from scikit-learn using matplotlib scatter plots. By passing c = wine.target, it color-codes the data points based on the three distinct wine cultivars (classes 0, 1, and 2), making it easy to visually inspect how well different chemical features separate the classes.

Key Observations & Quick Enhancements
While your approach works well for manual feature inspection, you can make these plots much easier to read with a couple of quick additions:

Add a Colorbar: Because wine.target contains integer labels, adding plt.colorbar() helps confirm which color corresponds to which class.

Use Seaborn for Automated Grouping: Instead of indexing columns manually (wine.data[:, index]), libraries like seaborn can handle categorical color mapping and legends automatically.

Here is how you can rewrite one of your plots using Seaborn for a cleaner look with a built-in legend:

Python
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.datasets import load_wine
import pandas as pd

# Load data into a pandas DataFrame for easier feature naming
wine = load_wine()
df = pd.DataFrame(wine.data, columns=wine.feature_names)
df['target'] = wine.target

# Create a clean scatter plot with a legend
plt.figure(figsize=(8, 6))
sns.scatterplot(
    x=df.columns[1], 
    y=df.columns[9], 
    hue='target', 
    palette='viridis', 
    data=df, 
    s=50
)
plt.title("Wine Dataset Feature Separation")
plt.show()
Want me to generate a full pairplot to visualize all features at once?

Yes
making the images side by side

To display your scatter plots side-by-side in a single row instead of vertically one after another, you can use Matplotlib's plt.subplots().

Here is how you can update your code to create a 1x3 grid of side-by-side plots:

Python
import matplotlib.pyplot as plt
from sklearn.datasets import load_wine

# Load dataset
wine = load_wine()

# Create a figure with 1 row and 3 columns
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

# Plot 1: Feature 1 vs Feature 9
scatter1 = axes[0].scatter(wine.data[:, 1], wine.data[:, 9], s=30, c=wine.target, cmap='viridis')
axes[0].set_xlabel(wine.feature_names[1])
axes[0].set_ylabel(wine.feature_names[9])
axes[0].set_title(f"{wine.feature_names[1]} vs {wine.feature_names[9]}")

# Plot 2: Feature 5 vs Feature 6
scatter2 = axes[1].scatter(wine.data[:, 5], wine.data[:, 6], s=30, c=wine.target, cmap='viridis')
axes[1].set_xlabel(wine.feature_names[5])
axes[1].set_ylabel(wine.feature_names[6])
axes[1].set_title(f"{wine.feature_names[5]} vs {wine.feature_names[6]}")

# Plot 3: Feature 0 vs Feature 3
scatter3 = axes[2].scatter(wine.data[:, 0], wine.data[:, 3], s=30, c=wine.target, cmap='viridis')
axes[2].set_xlabel(wine.feature_names[0])
axes[2].set_ylabel(wine.feature_names[3])
axes[2].set_title(f"{wine.feature_names[0]} vs {wine.feature_names[3]}")

# Add a single colorbar for all plots
fig.colorbar(scatter3, ax=axes, orientation='vertical', label='Wine Class')

# Adjust layout so labels don't overlap
plt.tight_layout()
plt.show()
What Changed?
plt.subplots(1, 3, figsize=(18, 5)): Creates 1 row of 3 subplots (axes[0], axes[1], axes[2]).

axes[i].set_xlabel() / axes[i].set_ylabel(): Sets axis labels specifically for each individual subplot.

fig.colorbar(...): Adds a shared legend/colorbar on the right side indicating the wine class for all three plots.

plt.tight_layout(): Automatically adjusts spacing so titles and axis labels don't collide.

keep the same structure wherever possible

To keep your original code structure as close to the original as possible while putting them side-by-side, you can use plt.subplot(1, 3, i) right before each block. This lets you keep almost every line of your original code intact:

Python
import matplotlib.pyplot as plt

# Set up the figure size so the plots fit side-by-side
plt.figure(figsize=(15, 4))

# Plot 1
plt.subplot(1, 3, 1)
plt.scatter(wine.data[:,1], wine.data[:,9], s = 30, c = wine.target) # c = wine.target is the part that does the color coding
plt.ylabel(wine.feature_names[9])
plt.xlabel(wine.feature_names[1])

# Plot 2
plt.subplot(1, 3, 2)
plt.scatter(wine.data[:,5], wine.data[:,6], s = 30, c = wine.target) # c = wine.target is the part that does the color coding
plt.ylabel(wine.feature_names[6])
plt.xlabel(wine.feature_names[5])

# Plot 3
plt.subplot(1, 3, 3)
plt.scatter(wine.data[:,0], wine.data[:,3], s = 30, c = wine.target) # c = wine.target is the part that does the color coding
plt.ylabel(wine.feature_names[3])
plt.xlabel(wine.feature_names[0])

# Clean up spacing and display all three together
plt.tight_layout()
plt.show()
Want me to show you how to save this side-to-side figure as an image file?

Yes






Gemini is AI and can make mistakes.

# BUILDING A LOOP THAT IS INTEROPPERABLE FOR DIFFERENT LAYERS TO TEST THE OPTIMAL NUMBER OF NODES FOR EACH LAYER

# Now build a loop to test how well different number of hidden layers performs

scores = {}

scores_list = []

l_range = range(4, 20, 1)

# The loop variable l below will iterate through the integers from 4 to 19

# (range(4, 20, 1)).

# This defines 3 hidden layers in the network

# All 3 layers are assigned the same number of neurons (l) in every iteration.

# Iteration 1 (l = 4): 3 hidden layers with 4 neurons each

# Iteration 2 (l = 5): 3 hidden layers with 5 neurons each

# ...

# Final Iteration (l = 19): 3 hidden layers with 19 neurons each



for l in l_range:

    print(l)

    mlp = MLPClassifier(hidden_layer_sizes=(l, l, l), max_iter=1000, random_state=30)  # do we need to change anything here???

    mlp.fit(X_train, y_train)

    y_pred = mlp.predict(X_test)

    scores[l] = metrics.accuracy_score(y_test,y_pred)

    scores_list.append(metrics.accuracy_score(y_test,y_pred))

The core logic of your loop is correct—it will successfully iterate through values of 
l from 4 to 19, train a 3-layer MLP with 
(l,l,l) architecture, and record the accuracy in both a dictionary and a list.

However, there are two important things to check or change to ensure your model runs properly and efficiently:

1. Feature Scaling (Crucial for MLPClassifier)
Neural networks are extremely sensitive to the scale of input features. If your features (in X_train and X_test) have vastly different ranges or units, the MLP might fail to converge or give poor accuracy, throwing a ConvergenceWarning.

Fix: Make sure you scale your data using StandardScaler before running this loop.

2. Code Optimization (Avoid Redundancy)
In your current code, you compute metrics.accuracy_score(y_test, y_pred) twice in every iteration. It is cleaner and more efficient to calculate it once and store it in a variable.

Refined Code
Here is the cleaned-up loop, along with the scaling step you should run beforehand:

Python
from sklearn.preprocessing import StandardScaler
from sklearn.neural_network import MLPClassifier
from sklearn import metrics

# 1. Always scale your data for neural networks!
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# 2. Run the loop using the scaled data
scores = {}
scores_list = []
l_range = range(4, 20, 1)

for l in l_range:
    print(f"Running for l = {l}...")
    mlp = MLPClassifier(hidden_layer_sizes=(l, l, l), max_iter=1000, random_state=30)
    
    # Train on scaled training data
    mlp.fit(X_train_scaled, y_train)
    
    # Predict on scaled test data
    y_pred = mlp.predict(X_test_scaled)
    
    # Calculate accuracy once per iteration
    acc = metrics.accuracy_score(y_test, y_pred)
    scores[l] = acc
    scores_list.append(acc)






Gemini is AI and can make mistakes.

# NOW WORKING ON DISPLAYING AN ACCURACY SCORE AND ACTIVITY #3 ON THE HOMEWORK

# Let's go with a 4 layer model

mlp = MLPClassifier(hidden_layer_sizes=(4,4), max_iter=1000, random_state=30)

mlp.fit(X_train, y_train)



predictions1 = mlp.predict(X_test)



# Now look at the accuracy of your predictions

print(confusion_matrix(y_test, predictions1)) # Confusion Matrix



# We will use the confusion matrix to determine the accuracy which is measured as the total

# Number of correct predictions divided by the total number of predictions.

accuracy = np.trace(confusion_matrix(y_test, predictions1)) / np.sum(confusion_matrix(y_test, predictions1))

print("Accuracy:", accuracy)

That’s a solid start using a Multi-Layer Perceptron (MLPClassifier) with two hidden layers of 4 nodes each (hidden_layer_sizes=(4,4)).

Your manual calculation of accuracy using the confusion matrix (np.trace(...) / np.sum(...)) works correctly! However, scikit-learn provides built-in shortcuts to make this cleaner:

Model Score: You can get the accuracy directly from the fitted model:

Python
accuracy = mlp.score(X_test, y_test)
print("Accuracy:", accuracy)
Accuracy Metric: Or use accuracy_score from sklearn.metrics:

Python
from sklearn.metrics import accuracy_score
print("Accuracy:", accuracy_score(y_test, predictions1))
To get a complete picture of your model's performance beyond just overall accuracy, it's usually helpful to look at precision, recall, and F1-score for each class.

Want me to show you how to add a detailed classification report and plot the training loss curve?

Yes
write code to take this file from C:/Users/jtgal/OEAS805/DATA/unknown_wine.csv to classify each wine into wine classes and then make a confusion matrix to see how well the classification did

Here is the complete Python code to load your dataset from C:/Users/jtgal/OEAS805/DATA/unknown_wine.csv, split the data, scale the features (which is especially important for neural network models like MLPClassifier), train the model, and evaluate it using a confusion matrix.

Python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neural_network import MLPClassifier
from sklearn.metrics import confusion_matrix, accuracy_score

# 1. Load the dataset
file_path = "C:/Users/jtgal/OEAS805/DATA/unknown_wine.csv"
df = pd.read_csv(file_path)

# 2. Separate features (X) and target classes (y)
X = df.drop(columns=['target'])
y = df['target']

# 3. Split data into training and testing sets (70% train, 30% test)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=30
)

# 4. Scale the features (Neural networks converge better when data is normalized)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# 5. Initialize and train the MLP Classifier
mlp = MLPClassifier(hidden_layer_sizes=(4, 4), max_iter=1000, random_state=30)
mlp.fit(X_train_scaled, y_train)

# 6. Make predictions on the test set
predictions1 = mlp.predict(X_test_scaled)

# 7. Evaluate performance
conf_matrix = confusion_matrix(y_test, predictions1)
accuracy = accuracy_score(y_test, predictions1)

print("Confusion Matrix:")
print(conf_matrix)
print("\nAccuracy:", accuracy)