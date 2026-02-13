import numpy as np
import matplotlib.pyplot as plt
from pathlib import Path

# Load the scrambled array (update the path if needed)
file = Path.home() / "Downloads" / "encoded_array.npy"
arr = np.load(r"C:\Users\thris\Downloads\encoded_array.npy")

# Ensure it's square and reshape correctly
n = arr.size
side = int(np.sqrt(n))
assert side * side == n, "Array cannot be reshaped into a square"

img = arr.reshape((side, side), order='C')  # Step that revealed half the face

#  Flip image horizontally (left-right)
img_full = np.fliplr(img)  # mirror image to complete the face

# Display completed image
plt.figure(figsize=(6, 6))
plt.imshow(img_full, cmap='gray', interpolation='nearest')
plt.title("Complete Happy Face (Horizontal Flip)")
plt.axis('off')
plt.show()
