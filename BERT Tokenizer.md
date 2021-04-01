### 참고문헌
* https://han-py.tistory.com/267
* https://albertauyeung.github.io/2020/06/19/bert-tokenization.html
* https://codlingual.tistory.com/98
* https://huggingface.co/transformers/glossary.html


# BERT Tokenizer 
* subword tokenizer의 일종으로 단어가 아닌 형태소(?) 단위로 분할됨
* 기존 토크나이저는 문맥에 상관없이 동일 단어 => 동일 임베딩이었으나, 버트의 경우 문맥에 따라 같은 단어라도 임베딩이 달라진다

## 기본 개념
1. input_ids: 문장을 토크나이즈해서 인덱스 값으로 변환. 버트에서는 단어를 subword 단위로 변환시키는 WordPieceTokenizer 활용
2. attention_mark: 패딩된 부분이 학습에 영향을 미치지 않도록 학습에 영향을 받는 토큰과 영향을 받지 않는 토큰을 구별해줌(1은 어텐션에 영향을 받는 토큰, 0은 받지 않는 토큰)
> <img width="663" alt="스크린샷 2021-04-01 오후 2 21 00" src="https://user-images.githubusercontent.com/74886546/113247200-7dca8800-92f5-11eb-8e49-524304fe5224.png">
3. token_type_ids(segment IDs): 문장간의 구분을 위해 쓰임. input문장이 하나면 segmentID는 모두 1이 되고 두개면 첫 문장은 0, 다음 문장은 1로 줘서 구분
> <img width="470" alt="스크린샷 2021-04-01 오후 2 34 05" src="https://user-images.githubusercontent.com/74886546/113248130-507ed980-92f7-11eb-8a61-e655c03922de.png">
4. 스폐셜 토큰: 문장의 시작과 끝 등을 표시하기 위해 다양한 토큰을 
> <img width="666" alt="스크린샷 2021-04-01 오후 2 30 28" src="https://user-images.githubusercontent.com/74886546/113247876-cf274700-92f6-11eb-8476-f6a9b7ce0dfc.png">


## encode_plus
* 버트 토크나이저 구현을 위한 함수
* text: 입력 텍스트
* add_special_tokens = bool: 시작점에 CLS, 끝에 SEP 추가됨
* max_length = MAX_LEN: 최대길이 지정해서 문장의 길이 맞춤
* pad_to_max_length: max_length에 따라 패딩 적용
* return_attention_mask: attention mask 생성
> <img width="529" alt="스크린샷 2021-04-01 오후 2 34 33" src="https://user-images.githubusercontent.com/74886546/113248177-62f91300-92f7-11eb-8ffa-237defc63701.png">
><img width="659" alt="스크린샷 2021-04-01 오후 2 35 24" src="https://user-images.githubusercontent.com/74886546/113248250-815f0e80-92f7-11eb-92f6-42ab0c870722.png">

## 변환 과정
<img width="657" alt="스크린샷 2021-04-01 오후 2 36 19" src="https://user-images.githubusercontent.com/74886546/113248303-a05da080-92f7-11eb-8b0f-6e165bbd8244.png"



