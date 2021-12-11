# final_project
1. Explanation of hyperparameters

[Loss] : torch.nn.CrossEntropyLoss

모델이 추측한 연예인의 레이블과 실제 연예인의 레이블의 Cross Entropy로 손실을 측정합니다.

[Optimizer] : torch.optim.Adam

Learning Rate = 0.001

[Training Data]

Epochs = 20

Batch Size = 16

[Data Augmentation]

1-1) torchvision.transforms.RandomHorizontalFlip : p=1.0          

원본 Training 데이터를 좌우 대칭시킨 데이터셋을 Training 데이터셋에 추가합니다.

1-2) torchvision.transforms.Pad                  : padding=5     -> torchvision.transforms.Resize : 원본 이미지 크기

원본 Training 데이터의 외곽에 5픽셀의 수치가 0인 데이터를 추가한 뒤, 원본 이미지의 크기와 똑같도록 크기를 재조정한 데이터셋을 Training 데이터셋에 추가합니다.

1-3) torchvision.transforms.CenterCrop           : size=5        -> torchvision.transforms.Resize : 원본 이미지 크기

원본 Training 데이터의 외곽에 5픽셀의 수치만큼의 이미지를 삭제한 뒤, 원본 이미지의 크기와 똑같도록 크기를 재조정한 데이터셋을 Training 데이터셋에 추가합니다.

[Learning Rate Scheduler] : torch.optim.lr_scheduler.ReduceLROnPlateau

optimizer = optimizer

patience = 3

factor = 0.1

[Test Data]

Batch Size = 4

Test Loss를 측정하여, 세 번 연속 Loss가 감소하지 않을 경우, torch.Adam Optimizer의 Learning Rate를 1/10로 감소합니다.

훈련과 테스트는 ipynb 파일에서 진행하여서, 따로 command가 존재하지 않습니다.

데이터 링크는 구글 드라이브 링크를 올려드립니다.

https://drive.google.com/drive/folders/1fRh82UCCVBBwq8Aapn0efA7iD6ribjQm?usp=sharing

해당 드라이브에서 AI 폴더에 있는 데이터는 원본 이미지들이 있는 폴더입니다.

predicted_face 폴더는 원본 이미지에서 1차 얼굴 추출을 한 결과 데이터들이 저장되어 있는 폴더입니다.

final_face 폴더는 1차 얼굴 이미지에서 2차 얼굴 추출을 한 결과 데이터들이 저장되어 있는 폴더입니다.

quiz 폴더는 2차 얼굴 이미지에서 눈, 코, 입 데이터를 추출하여 저장되어 있는 폴더입니다.

quiz 폴더에는 training 데이터와 test 데이터가 현재 섞여 있는 상태이며, test_dl.pickle 파일에 테스트용 데이터들을 저장해두었습니다.

이미지 출력을 위해 ipynb 파일에서 코드 작업을 진행하였고, 파이썬 파일에서 이미지를 출력하는 것과 ipynb 파일에서 이미지를 출력하는 것에 다소 차이가 있습니다.

코드의 이해를 위해 ipynb 파일과 데이터 처리에 필요했던 코드들을 함께 올려드립니다.
