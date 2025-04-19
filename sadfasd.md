```python
import os
import shutil
from PIL import Image
from sklearn.metrics import accuracy_score
from torchvision import datasets, transforms
from torch.utils.data import Dataset, DataLoader
from transformers import ViTImageProcessor, ViTForImageClassification, Trainer, TrainingArguments
import torch
import random
import time

start_time = time.time()

# ✅ 경로 설정
base_path = r"C:\Users\hwiya\Unsupervised Learning\Service-Learning"
image_dir = os.path.join(base_path, "raw_images")  # 190장 원본 이미지 (이미 이물질/정상으로 나눠져 있음)
labeled_dir = os.path.join(base_path, "labeled_apples")
train_dir = os.path.join(labeled_dir, "train")
val_dir = os.path.join(labeled_dir, "val")
test_dir = os.path.join(base_path, "test")  # 분류 대상 이미지
output_dir = os.path.join(base_path, "predicted_output")
os.makedirs(output_dir, exist_ok=True)

# ✅ 클래스 정의
class_names = ["normal_apple", "foreign_apple"]
num_labels = len(class_names)

# ✅ transform 정의
processor = ViTImageProcessor.from_pretrained("google/vit-base-patch16-224-in21k")
transform = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.ToTensor(),
    transforms.Lambda(lambda x: processor(images=x, return_tensors="pt")["pixel_values"][0])
])

# ✅ 데이터 수동 분할 (130/35 for normal, 20/5 for foreign)
def split_and_copy(source, class_name, train_n, val_n):
    files = os.listdir(source)
    random.shuffle(files)
    train_files = files[:train_n]
    val_files = files[train_n:train_n + val_n]

    for subset, subset_files in [("train", train_files), ("val", val_files)]:
        target = os.path.join(labeled_dir, subset, class_name)
        os.makedirs(target, exist_ok=True)
        for file in subset_files:
            shutil.copy(os.path.join(source, file), os.path.join(target, file))

split_and_copy(os.path.join(image_dir, "normal_apple"), "normal_apple", 130, 35)
split_and_copy(os.path.join(image_dir, "foreign_apple"), "foreign_apple", 20, 5)

# ✅ 데이터셋 로드
train_dataset = datasets.ImageFolder(train_dir, transform=transform)
val_dataset = datasets.ImageFolder(val_dir, transform=transform)

# ✅ 모델 로드
model = ViTForImageClassification.from_pretrained(
    "google/vit-base-patch16-224-in21k", num_labels=num_labels
)

# ✅ 학습 인자
training_args = TrainingArguments(
    output_dir=os.path.join(base_path, "vit_output"),
    evaluation_strategy="epoch",
    save_strategy="epoch",
    per_device_train_batch_size=8,
    per_device_eval_batch_size=8,
    num_train_epochs=4,
    load_best_model_at_end=True,
    metric_for_best_model="accuracy",
    logging_dir=os.path.join(base_path, "logs"),
)

# ✅ 평가 함수
def compute_metrics(p):
    preds = torch.argmax(torch.tensor(p.predictions), axis=1)
    return {"accuracy": accuracy_score(p.label_ids, preds)}

# ✅ 학습
trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=train_dataset,
    eval_dataset=val_dataset,
    compute_metrics=compute_metrics
)

trainer.train()
model.save_pretrained(os.path.join(base_path, "vit_final"))

# ✅ 테스트셋 클래스
test_transform = transform
class TestDataset(Dataset):
    def __init__(self, folder, transform):
        self.paths = [os.path.join(folder, f) for f in os.listdir(folder) if f.lower().endswith(('.jpg', '.png'))]
        self.transform = transform

    def __len__(self):
        return len(self.paths)

    def __getitem__(self, idx):
        path = self.paths[idx]
        image = Image.open(path).convert("RGB")
        return self.transform(image), path

# ✅ 테스트셋 로딩 및 분류
model.eval()
test_dataset = TestDataset(test_dir, test_transform)
test_loader = DataLoader(test_dataset, batch_size=1)

normal_count = 0
foreign_count = 0

with torch.no_grad():
    for img_tensor, path in test_loader:
        output = model(img_tensor)
        pred_label = torch.argmax(output.logits, dim=1).item()
        class_name = class_names[pred_label]

        if pred_label == 0:
            normal_count += 1
        else:
            foreign_count += 1

        dest = os.path.join(output_dir, class_name)
        os.makedirs(dest, exist_ok=True)
        shutil.copy(path[0], os.path.join(dest, os.path.basename(path[0])))

end_time = time.time()
all_time = end_time - start_time

# ✅ 결과 출력
print(f"경과 시간: {all_time}")
print(f"✅ 일반 사과: {normal_count}장")
print(f"⚠️ 이물질 사과: {foreign_count}장")
print(f"📂 분류 결과 저장 위치: {output_dir}")
```
