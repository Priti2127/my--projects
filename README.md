🧠 Java ML Project: Customer Churn Prediction using Tribuo
📋 Overview

This project demonstrates an end-to-end Machine Learning pipeline built entirely in Java using Tribuo
, Oracle’s ML library.
The goal is to predict customer churn (whether a user will leave a service) based on demographic and behavioral data.

It covers:

Data ingestion and preprocessing

Model training and evaluation

Model persistence (saving/loading models)

REST API for serving predictions

⚙️ Tech Stack
Category	Technology
Language	Java 17
ML Framework	Tribuo
Build Tool	Maven
API Layer	Spring Boot
Data Storage	CSV / MySQL
Visualization	JFreeChart / Matplotlib (via Python bridge, optional)
Containerization	Docker (optional)
🧩 Features

✅ Load and preprocess structured CSV data
✅ Train supervised ML models (e.g., Logistic Regression, Random Forest)
✅ Evaluate models with accuracy, precision, recall, and F1 metrics
✅ Export trained model to file for later inference
✅ REST endpoint to make real-time predictions

🗂️ Project Structure
tribuo-churn-prediction/
├── src/
│   ├── main/
│   │   ├── java/com/example/tribuo/
│   │   │   ├── Main.java
│   │   │   ├── DataLoader.java
│   │   │   ├── ModelTrainer.java
│   │   │   ├── PredictorService.java
│   │   │   ├── RestController.java
│   │   └── resources/
│   │       └── churn_data.csv
├── pom.xml
├── README.md
└── LICENSE

🚀 Getting Started
1️⃣ Clone the repository
git clone https://github.com/<your-username>/tribuo-churn-prediction.git
cd tribuo-churn-prediction

2️⃣ Build with Maven
mvn clean package

3️⃣ Run the application
mvn spring-boot:run

4️⃣ Access the API

Once the Spring Boot server is running:

POST http://localhost:8080/predict
Body:
{
  "age": 34,
  "tenure": 5,
  "balance": 4200.50,
  "numOfProducts": 2,
  "isActiveMember": true
}

📊 Example Output
Prediction: Customer likely to churn (Probability: 0.83)
Model: Logistic Regression (Tribuo v4.x)
Accuracy: 87.2%

🧮 Model Training Example
var dataSource = new CSVLoader<>(new LabelFactory()).loadDataSource("churn_data.csv", "churn");
var splitter = new TrainTestSplitter<>(dataSource, 0.7, 1L);
var trainData = new MutableDataset<>(splitter.getTrain());
var testData = new MutableDataset<>(splitter.getTest());

var trainer = new LogisticRegressionTrainer();
var model = trainer.train(trainData);

var evaluator = new LabelEvaluator();
var evaluation = evaluator.evaluate(model, testData);
System.out.println(evaluation.toString());

📦 Dataset

You can use:

Telco Customer Churn dataset (Kaggle)

Save it as churn_data.csv in the resources/ folder.

🧰 Future Enhancements

Add deep learning model integration (via ONNX or TensorFlow export)

Implement web dashboard for visual insights

CI/CD pipeline for model retraining

Deploy prediction API to AWS/GCP/Azure

🧑‍💻 Author

Your Name
📧 your.email@example.com

🌐 LinkedIn
 • GitHub

📜 License

This project is licensed under the MIT License — see the LICENSE
 file for details.

🏆 Resume Bullet Example

• Built an end-to-end Java ML system using Tribuo for customer churn prediction.
• Trained and deployed models via Spring Boot REST API (87% accuracy).
• Implemented modular architecture with Maven, Docker, and MySQL persistence.
