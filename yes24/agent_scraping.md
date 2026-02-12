# Yes24 베스트셀러 스크래핑

이 문서는 Yes24의 주간 베스트셀러 데이터를 수집하는 과정을 설명합니다.

## 1. 데이터 수집 목표

Yes24의 주간 베스트셀러 목록에서 다음 정보를 수집합니다.

*   순위 (Rank)
*   제목 (Title)
*   저자 (Author)
*   출판사 (Publisher)
*   발행일 (Publication Date)
*   가격 (Price)
*   책 소개 (Description)
*   이미지 URL (Image URL)

## 2. 네트워크 정보

### URL

*   **http://www.yes24.com/24/Category/BestSeller**

### Request Headers

일반적인 브라우저 헤더를 사용하여 요청합니다. User-Agent를 설정하여 차단을 피합니다.

```
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36
```

### Payload

별도의 Payload는 필요하지 않습니다. (GET 요청)

## 3. 응답 데이터 예시 (HTML 일부)

```html
<li class="num1">
    <p class="best_rnk">
        <span class="rib_best">1</span>
    </p>
    <div class="bst_book">
        <a href="/Product/Goods/124799011" class="img_best">...</a>
        <a href="/Product/Goods/124799011" class="name_best">...</a>
    </div>
    <div class="bst_cont">
        <div class="bst_name">
            <a href="/Product/Goods/124799011" class="name_b">나의 돈키호테</a>
        </div>
        <div class="bst_pub_info">
            <span class="bst_auth">
                <a href="/Search?domain=ALL&query=김호연">김호연</a>
            </span>
            <span class="line">|</span>
            <span class="bst_pub">
                <a href="/Search?domain=ALL&query=나무옆의자">나무옆의자</a>
            </span>
            <span class="line">|</span>
            <span class="bst_date">2024년 01월</span>
        </div>
        <div class="bst_price">
            <span class="price_b">15,750원</span>
        </div>
        <div class="bst_desc">
            <a href="/Product/Goods/124799011">...</a>
        </div>
    </div>
</li>
```

## 4. 데이터 저장

수집된 데이터는 `pandas` DataFrame으로 변환된 후 `bestsellers.csv` 파일로 저장됩니다.
