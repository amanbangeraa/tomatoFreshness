import cv2
import numpy as np
from tensorflow.keras.models import load_model

# Load your trained model
model = load_model("tomato_freshness_model.h5")

# Class names in the same order used during training
class_names = ['Damaged', 'Old', 'Ripe', 'Unripe']

# Image size used during training
IMG_SIZE = (224, 224)

# Open webcam
cap = cv2.VideoCapture(0)

if not cap.isOpened():
    print("❌ Could not open webcam.")
    exit()

print("✅ Press 'q' to quit")

while True:
    ret, frame = cap.read()
    if not ret:
        print("❌ Failed to grab frame")
        break

    # Preprocess frame
    img = cv2.resize(frame, IMG_SIZE)
    img = img.astype("float32") / 255.0
    img = np.expand_dims(img, axis=0)

    # Predict
    preds = model.predict(img)
    label = class_names[np.argmax(preds)]
    confidence = np.max(preds)

    # Display result
    text = f"{label} ({confidence*100:.1f}%)"
    cv2.putText(frame, text, (20, 40), cv2.FONT_HERSHEY_SIMPLEX, 1.2, (0, 255, 0), 2)

    cv2.imshow("🍅 Tomato Freshness Detector", frame)

    # Exit condition
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
# tomatoFreshness
