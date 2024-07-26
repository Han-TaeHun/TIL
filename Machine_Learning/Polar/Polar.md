
https://pola.rs/

`Polars`는 `pandas`와 유사한 기능을 제공하는 고성능 데이터프레임 라이브러리로, 특히 대용량 데이터 처리에 최적화되어 있습니다. `polars`는 Rust 언어로 작성되어 있으며, Python 인터페이스를 통해 사용할 수 있습니다. 속도와 메모리 효율성 면에서 탁월한 성능을 자랑합니다.

### 주요 특징:

1. **고성능**:
    - `polars`는 Rust로 작성되어 있어 매우 빠른 데이터 처리 성능을 제공합니다. 특히 대규모 데이터셋을 다루는 데 유리합니다.
2. **메모리 효율성**:
    - 메모리 사용을 최적화하여, 메모리 사용량을 줄이면서 대용량 데이터를 효율적으로 처리할 수 있습니다.
3. **병렬 처리**:
    - 기본적으로 멀티코어 CPU를 활용한 병렬 처리를 지원하여 데이터 처리 속도를 극대화합니다.
4. **표현력**:
    - `polars`는 데이터 변환과 분석을 위한 다양한 함수와 메서드를 제공하여 복잡한 데이터 작업을 간단하게 표현할 수 있습니다.
    
5. **예제**

```python
import polars as pl

# 데이터프레임 생성
df = pl.DataFrame({
    "Name": ["Alice", "Bob", "Cathy"],
    "Age": [25, 30, 22],
    "Salary": [50000, 60000, 55000]
})

# 데이터프레임 출력
print(df)
```

![](https://velog.velcdn.com/images/hth623/post/8ae3a898-d512-4be2-a0a1-68bdacfd8efb/image.png)

```python
# 특정 열 선택
age_series = df["Age"]
print(age_series)
```

![](https://velog.velcdn.com/images/hth623/post/d6a04d5d-352c-4aa2-b5e4-3281f0488b29/image.png)


```python
# 열 변환 및 새로운 데이터프레임 생성
new_df = df.with_columns([
    (pl.col("Salary") * 1.1).alias("New_Salary")
])
print(new_df)
```

![](https://velog.velcdn.com/images/hth623/post/3f7a0d79-4322-4446-a9f4-b2907f8f3a27/image.png)


```python
# 필터링
filtered_df = df.filter(pl.col("Age") > 25)
print(filtered_df)
```

![](https://velog.velcdn.com/images/hth623/post/398e4a75-977e-415d-8ed5-35dcbcecb3d7/image.png)


```python
# 집계
aggregated_df = df.groupby("Name").agg([
    pl.col("Salary").mean().alias("Average_Salary")
])
print(aggregated_df)
```

![](https://velog.velcdn.com/images/hth623/post/ff9089e3-b17a-4c5d-88a7-856e0bf57468/image.png)


```python
# 예제 데이터프레임 생성
df = pl.DataFrame({
    "Name": ["Alice", "Bob", "Cathy"],
    "Age": [25, 30, 22]
})

# 'Status' 열에 모든 값이 'Active'인 새로운 열 추가
df = df.with_columns(pl.lit("Active").alias("Status"))

print(df)
```

![](https://velog.velcdn.com/images/hth623/post/5590b08d-5dca-431c-9601-8331539108d7/image.png)


### 주요 함수 및 메서드:

- **`pl.DataFrame`**: 데이터프레임을 생성하는 클래스.
- **`pl.col`**: 특정 열을 선택하는 표현식.
- **`pl.lit`**: 리터럴 값을 표현식으로 변환.
- **`with_columns`**: 열을 추가하거나 변환하여 새로운 데이터프레임을 생성.
- **`filter`**: 조건에 맞는 행을 필터링.
- **`groupby`**: 그룹화 및 집계 연산.
- **`agg`**: 집계 함수 적용.
- **`alias`**: 열 이름 변경.

### 비교: `Polars` vs `Pandas`:

- **성능**: `polars`는 Rust 기반으로 작성되어 `pandas`보다 훨씬 빠른 성능을 제공합니다.
- **병렬 처리**: `polars`는 기본적으로 병렬 처리를 지원하므로, 대용량 데이터셋을 빠르게 처리할 수 있습니다.
- **메모리 사용**: `polars`는 메모리 효율성을 높여 더 큰 데이터셋을 처리할 수 있습니다.
- **인터페이스**: `polars`는 `pandas`와 유사한 인터페이스를 제공하므로, `pandas` 사용자라면 쉽게 전환할 수 있습니다.

`polars`는 특히 성능이 중요한 작업에서 유용하며, 대용량 데이터셋을 다룰 때 매우 유리합니다. 데이터 처리와 분석 작업에서 높은 성능을 요구하는 사용자에게 추천되는 라이브러리입니다.