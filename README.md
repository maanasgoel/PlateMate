# PlateMate: Automated Nutrient Tracking

Upload a photo of a meal, and PlateMate identifies the foods on the plate and reports their nutrition: calories, protein, carbohydrates, and sugars. It's built for parents, schools, and anyone who wants an easy way to track what they eat.

## How it works

- **Dataset:** 480 photos across six food categories (apples, oranges, bananas, chips, cookies, yogurt), shot from front, side, top-down, and tilted angles so the model can recognize food in any orientation. Augmented with rotation, shifts, zoom, and flips, and split 70/15/15 into train, validation, and test sets.
- **Model:** a custom CNN plateaued around 60% validation accuracy, so we switched to transfer learning with MobileNetV2 (pretrained on ImageNet), followed by global average pooling, 20% dropout, and dense layers for the six classes. Trained for 20 epochs with Adam.
- **App:** the trained model is exported to TensorFlow Lite and runs in a lightweight web app that classifies the uploaded photo and shows its nutrition.

## Result

The final model classified all 72 held-out test images correctly.

## Report and poster

- Report: [PlateMate_Report.pdf](PlateMate_Report.pdf)
- Poster: [PlateMate_Poster.pdf](PlateMate_Poster.pdf)

## Files

- `DatasetScriptGenerationForESE3600FinalProject.ipynb`: dataset preparation
- `ESE3600ImageClassifierForProject.ipynb`: model training and evaluation
- `finalFoodFloat.tflite`: the trained model
- `index.html`, `classifer.js`, `styles.css`: the [web app](https://moshah122.github.io/PlateMate/)
