# 🌀 Topological Data Analysis (TDA) on MNIST: Digits 1 vs 8

This project explores how **Topological Data Analysis (TDA)** can be used to classify handwritten digits, specifically distinguishing between the digits **1** and **8** from the MNIST dataset. The goal is to leverage geometric/topological structure—beyond raw pixel values—using tools like persistent homology.

---

## 🧠 Summary

- 📚 **Dataset**: MNIST (filtered to digits 1 and 8)
- 📈 **Model**: Logistic Regression
- 🔍 **Features**: Extracted using persistent homology (from `ripser`)
- 📊 **Performance**:
  - **TDA-based accuracy on unseen data**: **99.5%**
  - **Raw pixel-based accuracy on unseen data**: **97.55%**

---

## 🔧 How It Works

1. **Data Loading**:
   - Uses `sklearn.datasets.fetch_openml` to load the MNIST dataset.
   - Filters to only include digits `1` and `8`.

2. **Image to Point Cloud**:
   - Each image is thresholded and converted to a point cloud in ℝ².

3. **Persistent Homology**:
   - Computes persistence diagrams (H₁) using `ripser`.
   - Captures topological loops (holes) in each image.

4. **Feature Extraction**:
   - Extracts 7 features:
     - Number of H₁ features (loops)
     - Longest and second-longest lifetimes
     - Birth and death times of the top two loops

5. **Classification**:
   - Trains `LogisticRegression` on extracted TDA features.
   - Evaluated on held-out test data and unseen examples.
   - Compared to a baseline model trained on raw pixel data.

---

## 📦 Dependencies

Install required packages using:

```bash
pip install ripser persim gudhi scikit-learn numpy
