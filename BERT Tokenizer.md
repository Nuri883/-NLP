### 참고문헌
https://han-py.tistory.com/267
https://albertauyeung.github.io/2020/06/19/bert-tokenization.html
https://codlingual.tistory.com/98
https://huggingface.co/transformers/glossary.html


# BERT Tokenizer 
* subword tokenizer의 일종으로 단어가 아닌 형태소(?) 단위로 분할됨
* 기존 토크나이저는 문맥에 상관없이 동일 단어 => 동일 임베딩이었으나, 버트의 경우 문맥에 따라 같은 단어라도 임베딩이 달라진다

## 버트 활용에 필요한 입력값
1. input_ids: 문장을 토크나이즈해서 인덱스 값으로 변환. 버트에서는 단어를 subword 단위로 변환시키는 WordPieceTokenizer 활용
2. attention_mark: 패딩된 부분이 학습에 영향을 미치지 않도록 학습에 영향을 받는 토큰과 영향을 받지 않는 토큰을 구별해줌(1은 어텐션에 영향을 받는 토큰, 0은 받지 않는 토큰)
> <img width="663" alt="스크린샷 2021-04-01 오후 2 21 00" src="https://user-images.githubusercontent.com/74886546/113247200-7dca8800-92f5-11eb-8e49-524304fe5224.png">
3. token_type_ids(segment IDs): 문장간의 구분을 
