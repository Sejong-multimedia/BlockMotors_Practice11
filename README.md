#1. KIP17Storage : Override => 컨트랙트에 직접 추가 (다중URI)


#2. TokenURI 구조체, TokenURI 맵핑 추가

    struct TokenURI {
        string URI_Register;    // 토큰URI(등록용)
        string URI_Trade;       // 토큰URI(거래용)
    }

    mapping(uint256 => TokenURI) private _tokenURIs


#3. CarDataWithTokenId 구조체 수정

    struct CarDataWithTokenId {                         // getOwnedTokenIds()
        uint256 TokenId;        // 토큰ID
        string brand;           // 제조사
        string model;           // 모델
        string year;            // 연식
        string licenseNum;      // 차량번호
        string registerNum;     // 등록번호
        string fuel;            // 사용연료
        string cc;              // 배기량
        string URI_Register;    // 토큰URI(등록용)
        string URI_Trade;       // 토큰URI(거래용)
    }


#4. getCarNFT( ), getOwnedTokenIds( ) 반환값 수정

(기존) CarData구조체+tokenURI 반환 =>
(변경) CarData구조체+TokenURI구조체 반환

#5. tokenURI( ) 함수 더 이상 작동안함
(변경) _TokenURI[tokenId].URI_Register, _TokenURI[tokenId].URI_Trade 로 조회
