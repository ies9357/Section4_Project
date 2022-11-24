# 흉부 X-ray 이미지를 통한 코로나 및 폐질환 판별 딥러닝 모델 개발
##    1. 프로젝트에서 풀고자 하는 문제 : **코로나와 폐질환의 증상이 비슷함**으로 인해, 환자와 의료진에게 **발생할 수 있는 여러 문제들**
1. **[환자]** 본인이 가지는 질병에 대한 **치료시기를 놓치는 문제**
ex). 환자가 가진 폐질환을 코로나로 오인하게 되는 경우, 선별진료소에서 코로나 검사를 받고 검사결과를 기다리는 동안 자신이 가진 폐질환이 악화될 수 있음.
2. **[의료진]** 진단 검사에 있어, **인력 낭비** 발생
ex). 환자의 오인으로 인해 폐질환을 가진 환자가 코로나 선별진료소에 방문하여 코로나 검사를 받게 되면, 의료진 입장에서는 불필요한 업무를 수행하게 되는 꼴임. 
3. **가설**
    1. **딥러닝 모델이** 4가지 클래스에 대한 **X-ray 이미지 패턴을 학습**해서 **환자 상태를 잘 분류**할 수 있다.
        
        
        
##    2. 프로젝트 진행과정 **(기간 : 2022.07.25 - 2022.07.28)**
1. **데이터 선정 및 EDA 진행, 가설 설정**
2. **[데이터 전처리]** X-ray 이미지의 데이터 프레임 구축, 데이터 프레임 & 이미지 전처리
3. **[모델 구성 및 학습]** 사전학습 모델을 활용한 모델구성, callback 함수 구성, 모델학습 진행
4. **[모델평가 및 저장]** 학습된 모델을 테스트 셋으로 평가한 뒤 모델 저장
    
    
    
##    3. 데이터 셋 설명
1. 데이터 : 흉부 X-ray 이미지
    1. 출처 : [https://bit.ly/3U0FYUY](https://bit.ly/3U0FYUY)
2. 데이터 종류 : 4가지 상태의 흉부 X-ray 이미지

    ![image](https://user-images.githubusercontent.com/102272580/203721127-e310187b-bcb4-4598-83f5-471d6fe3700a.png)

3. 데이터 크기(pixels) : 299(높이) X 299(너비)
4. 라벨 별 데이터 개수
    1. 표


        | 상태 | 데이터 개수(개) |
        | --- | --- |
        | 정상 상태(Normal) | 10192 |
        | 코로나 감염 상태(COVID) | 3616 |
        | 바이러스성 폐렴(Viral pneumonia) | 1345 |
        | 폐 음영(Lung Opacity) | 6012 |
    2. 파이차트
        1. 정상상태 : 라벨 비율의 거의 절반을 차지함
        2. COVID : 라벨 비율의 17.1% 밖에 차지하지 못함
            1. 불균형 데이터임을 알 수 있음

        ![image](https://user-images.githubusercontent.com/102272580/203721277-54d5deff-7e4e-45b4-aaa3-ef0eefaf64a5.png)



##    4. 문제상황 해결과정
1. 코로나 및 폐질환 판별 딥러닝 모델 제작 및 테스트
    1. **데이터 선정 및 EDA 진행, 가설 설정**
    2. **[데이터 전처리]** X-ray 이미지의 데이터 프레임 구축, 데이터 프레임 & 이미지 전처리
    3. **[모델 구성 및 학습]** 사전학습 모델을 활용한 모델구성, callback 함수 구성, 모델학습 진행
    4. **[모델평가 및 저장]** 학습된 모델을 테스트 셋으로 평가한 뒤 모델 저장

2. 제작한 딥러닝 모델을 이용한 이미지 분류

    ![image](https://user-images.githubusercontent.com/102272580/203722374-0d165171-6884-4796-be15-7f0f1867d91b.png)

3. 딥러닝 분류 결과에 맞는 병원 방문 및 치료법 적용



##    5. 프로젝트 결과
1. **[정확도]** Training set - 0.9819, Validation set - 0.9423, Test set - 0.9396
2. **F1 score (Test set 이미지 1059개 기준)**
    1. 모든 클래스[코로나, 정상상태, 바이러스성 폐렴, 폐 음영]에 대해 0.91 이상
    2. 특히, 희귀 케이스인 코로나와 바이러스성 폐렴에서의 분류성능이 양호함



##    6. 한계점 및 해결방안
1. 한계점
    1. 사전학습 모델과 다른 사람들의 코드를 상당수 인용
    2. 데이터 셋 - 인종이나 나이, 성별 등에 대한 데이터가 없었음
2. 해결방안
    1. 딥러닝 관련 기본지식 및 활용경험을 더 쌓는다.
    2. 데이터 셋을 searching을 통해 구하거나 데이터 셋을 생성할 수 있는 GAN과 같은 기술을 활용하여 인종, 나이, 성별 등에 대한 다양한 이미지셋을 확보한 후 딥러닝 모델을 최적화 한다.
