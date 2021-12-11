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
