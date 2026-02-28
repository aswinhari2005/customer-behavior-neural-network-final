# 🎬 EXECUTION VIDEO SCRIPT
## Neural Network Customer Buying Behavior Prediction
### Estimated Duration: 12–15 minutes

---

## 🎙️ INTRO  [0:00 – 0:45]

*[Screen: Show project title slide or blank Colab notebook]*

**Say:**
"Hi! In this video I'll be walking you through my Industry Project — A Neural Network Approach 
to Analyse Customer Metrics and Predict Buying Trends.

We've built a Multilayer Perceptron neural network using Apache PySpark on Google Colab that 
achieves 99.5% accuracy in predicting whether a customer is a High Value or Low Value buyer.

I'll walk you through all four steps: data preprocessing, model training, evaluation and tuning, 
and finally deployment. Let's get started."

---

## 📦 STEP 1 — Data Preprocessing  [0:45 – 3:00]

*[Screen: Open the Colab notebook, scroll to Cell 1]*

**Say:**
"We start by installing PySpark and creating our Spark session. This is what enables us to 
process large datasets at scale — the same infrastructure used in enterprise data pipelines."

*[Run Cell 1 — show Spark version output]*

"Now let's upload our dataset. We're using the Customer Personality Analysis dataset from Kaggle 
— it has 2,240 customer records with demographics, purchase history, and campaign response data."

*[Run Cell 2 — show file upload and shape output]*

"Let's explore the data quickly."

*[Run Cell 3 — show columns, dtypes, missing values]*

"You can see we have 29 original features. There are 24 missing values in the Income column 
which we'll handle by dropping those rows."

*[Run Cell 4 — feature engineering]*

"Here's where we engineer our key features. We create Age from Year_Birth, TotalSpend by 
summing all product category spending, TotalPurchases across all channels, and our target 
variable — HighValueCustomer — which is 1 if the customer's spending is in the top 40%."

"You can see the class distribution is roughly balanced — important for unbiased training."

*[Run Cells 5, 6, 7]*

"We use VectorAssembler to combine our 11 features into a single vector, then StandardScaler 
to normalize them — essential for neural network convergence. Finally, we split 80% for 
training and 20% for testing."

---

## 🧠 STEP 2 — Model Training  [3:00 – 6:00]

*[Scroll to Cell 8]*

**Say:**
"Before training, let's visualize our network architecture."

*[Run Cell 8 — show neural network diagram]*

"This is our MLP: 11 input neurons — one per feature — feeding into a hidden layer of 16 
neurons, then 8 neurons, and finally 2 output neurons representing our two classes: 
Low Value and High Value customer."

*[Run Cell 9]*

"Our key hyperparameters: 150 maximum iterations, learning rate of 0.03, and a mini-batch 
size of 64."

*[Run Cell 10 — show training starting]*

"Training is in progress... The model is adjusting its weights through backpropagation to 
minimize classification error."

*[Show training complete message and time]*

"Training completed in under 2 minutes. Let's look at the predictions."

*[Run Cell 11 — show predictions DataFrame]*

"Here you can see the raw predictions alongside the actual labels and probability scores. 
The model outputs a probability for each class — notice how confident it is, with most 
probabilities close to 0 or 1."

*[Run Cell 12 — show accuracy]*

"99.5% accuracy on our first run. Let's look deeper."

*[Run Cell 13 — show weight distribution plot]*

"This histogram shows our model's weight distribution — it's centered near zero with a 
healthy spread, which indicates the model hasn't overfit."

---

## 📊 STEP 3 — Evaluation & Tuning  [6:00 – 10:00]

*[Scroll to Cell 14]*

**Say:**
"Now let's evaluate comprehensively across all four metrics."

*[Run Cell 14 — show evaluation report]*

"Accuracy: 99.5%. Precision: 99.5% — meaning when the model predicts High Value, it's 
correct 99.5% of the time. Recall: 99.4% — meaning we're catching 99.4% of all actual 
High Value customers. F1 Score: 99.4% — the harmonic mean confirming balanced performance."

*[Run Cell 15 — show confusion matrix]*

"The confusion matrix confirms this. You can see the vast majority of predictions fall on 
the diagonal — correct classifications. The off-diagonal cells represent the very few 
misclassifications."

*[Run Cell 16 — show feature importance]*

"This is one of the most insightful results. Feature importance using the permutation method."

"The gold bar stands out immediately — TotalSpend has an importance score of 0.2202, making 
it by far the most influential feature. TotalPurchases is second at 0.0552, and Income third 
at 0.0300."

"What this tells the business is powerful: a customer's actual spending behavior predicts 
their future value far better than demographic data. Age, marital status, number of children 
— these contribute almost nothing. The implication is that marketing should focus on 
re-engaging past big spenders, not targeting by demographics."

*[Run Cell 17 — hyperparameter tuning]*

"Let's now tune the model. We test four combinations of architecture and learning rate."

*[Show results printing one by one]*

"Both our original architecture and the larger 32-neuron variant achieve 99.5% at their 
optimal learning rates. We keep our simpler model — same accuracy, lower complexity."

*[Run Cell 18 — show interactive widget]*

"Now the interactive predictor. This is a live demo — I can adjust any customer attribute 
using these sliders and dropdowns."

*[Demonstrate: Set high income, high spend, high purchases — click predict]*

"High spending, high income, many purchases — and the model predicts High Value Customer 
with 98% confidence."

*[Demonstrate: Set low values — click predict]*

"Low spend, few purchases — model correctly predicts Low Value with high confidence."

---

## 🚀 STEP 4 — Deployment  [10:00 – 12:30]

*[Scroll to Cell 19]*

**Say:**
"Step 4 is deployment. We save the trained model."

*[Run Cell 19 — show model saved]*

"The model is persisted to disk in PySpark's native format, ready to be loaded into any 
production Spark environment."

*[Run Cell 20 — load and verify]*

"We reload the model and verify it still achieves 99.5% — confirming the save/load cycle 
is working perfectly."

*[Run Cell 21 — show final neural network diagram]*

"Here's our final annotated neural network diagram. You can see the three starred features — 
TotalSpend, TotalPurchases, and Income — highlighted in gold as the top predictors feeding 
into the network."

*[Run Cell 22 — show dashboard]*

"Finally, our customer insights dashboard. Six panels giving a complete picture:
- Top left: Spend vs Income shows a clear cluster separation between High and Low value customers.
- Top center: Age distributions show High Value customers skew slightly older.
- Top right: Prediction confidence — almost all predictions are near 0 or 1, showing the model is very decisive.
- Bottom left: Purchases boxplot clearly separates the two segments.
- Bottom center: Recency vs prediction score — recent purchasers tend to score as High Value.
- Bottom right: Our metrics bar chart confirming 99.5% across all measures."

*[Run Cell 23 — download outputs]*

"And we download all outputs — confusion matrix, feature importance chart, neural network 
diagram, and dashboard — as a zip file."

---

## 🎯 WRAP-UP  [12:30 – 13:30]

*[Screen: Show final dashboard or title slide]*

**Say:**
"To summarize what we've built:

A complete end-to-end Neural Network pipeline in PySpark that achieves 99.5% accuracy 
in predicting customer buying behavior.

The three key takeaways from this project:

One — Behavioral data dominates. TotalSpend alone is 4 times more predictive than any 
other feature, including income and demographics.

Two — MLP neural networks are highly effective for structured retail data classification 
when properly preprocessed with scaling and feature engineering.

Three — PySpark makes this scalable. The same pipeline can handle millions of records 
in a production environment with no code changes.

Thank you for watching. The complete code is available on GitHub, and all outputs have 
been saved. If you have any questions, feel free to reach out."

---

## 📋 RECORDING CHECKLIST

Before recording:
- [ ] Run ALL cells top to bottom once to confirm no errors
- [ ] Clear all outputs (Runtime > Restart and Clear Output)
- [ ] Start screen recorder (OBS / Loom / built-in)
- [ ] Set Colab to full screen
- [ ] Increase font size in browser (Ctrl + "+") for visibility

During recording:
- [ ] Speak clearly and at moderate pace
- [ ] Pause briefly after each cell output appears
- [ ] Point to specific numbers when discussing metrics
- [ ] Demo the interactive widget live (Cell 18)
- [ ] Show the dashboard clearly (zoom in if needed)

After recording:
- [ ] Trim any long pauses
- [ ] Add captions if required
- [ ] Export at 1080p minimum
