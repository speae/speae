To insert a mathematical formula we use the dollar symbol $, as follows:

Euler's identity: 

$ e^{i \pi} + 1 = 0 $

To isolate and center the formulas and enter in math display mode, we use 2 dollars symbol:

$$
...
$$

Euler's identity: $$ e^{i \pi} + 1 = 0 $$

# 수식
$ \alpha = \beta $

# 수식(독립된 문단으로 표현)
$$ \alpha = \beta $$

#%% md

# 수열
$1, 2, 3, 4$

#%% md

###### 아래첨자는 인덱스
$x_1, x_2, x_3, x_4, x_5, x_6$

#%% md

###### 수열이 아주 길거나 수열 길이가 숫자가 아닌 문자에는 ... 기호를 사용하여 다음처럼 가운데 부분을 생략할 수 있음
$x_1, x_2, ..., x_N$

#%% md

# 집합
{1, 2, 3, 4}

{$x_1, x_2, x_3, x_4, x_5, x_6$}

###### 집합 또한 원소가 많은 경우 가운데 생략 가능
{$x_1, x_2, x_3, x_4, x_5, x_6$}

$= x_{1:N}$

$=$ {$x_i$}$_{N}$

#%% md

# 집합 기호

###### 1, -2, 3.14와 같은 실수 전체 집합인 경우
###### 어떤 숫자 x가 실수면 집합 R에 포함
$$ x \in \mathbb{R} $$

###### 만약 두 숫자가 이루어진 숫자 쌍 (x<sub>1</sub>, x<sub>2</sub>)가 있고
###### 각 숫자 x<sub>1</sub>, x<sub>2</sub>가 모두 실수라면 다음처럼 표시
$(x_1, x_2) \in \mathbb{R} \times \mathbb{R}$

$=(x_1 , x_2) \in \mathbb{R}^2$

#%% md

# 수열의 합과 곱
###### 수열을 더하거나 곱하는 연산을 짧게 줄여씀
###### 시그마; ∑(sum), 파이; ∏(product)
$\sum_{i=1}^{N} x_i = x_1 + x_2 + ... + x_N$

$\prod_{i=1}^{N} x_i = x_1 \cdot x_2 \cdot ... \cdot x_N$

###### 1부터 4까지 더해야 하는 경우
$\sum_{i=1}^{4} i = 1 + 2 + 3 + 4$

###### 10부터 90까지 10씩 증가하는 수열을 모두 더해야 하는 경우
$
\sum_{k=1}^{9} 10k = 10 \cdot 1 + 10 \cdot 2 + ... + 10 \cdot 9
= 10 + 20 + ... + 90
$

###### 10부터 20까지의 수를 모두 곱하는 식
$\prod_{i=10}^{20} i = (10) \cdot (11) ... (20)$

###### 합이나 곱을 중첩하여 여러 번 쓰는 경우
$\sum_{i=1}^{N}(\sum_{j=1}^{M} x_{ij}) = \sum_{i=1}^{N}\sum_{j=1}^{M} x_{ij}$

###### 합과 곱을 중첩한 수식
$\sum_{i=1}^{2}\sum_{j=1}^{3} x_{ij} = \sum_{i=1}^{3}(\sum_{j=1}^{3} (i + j))$

$= \sum_{i=1}^{2} ((i + 1) + (i + 2) + (i + 3))$

$= ((1 + 1) + (1 + 2) + (i + 3)) + ((2 + 1) + (2 + 2) + (2 + 3))$

$\prod_{m=1}^{3}\prod_{n=1}^{2} (m + 2n)$

$= \prod_{m=1}^{3}(\prod_{n=1}^{2} (m + 2n))$

$= \prod_{m=1}^{3}((m + 2 \cdot 1) \cdot (m + 2 \cdot 2))$

$= ((1 + 2 \cdot 1) \cdot (1 + 2 \cdot 2)) \cdot ((2 + 2 \cdot 1) \cdot (2 + 2 \cdot 2)) \cdot ((3 + 2 \cdot 1) \cdot (3 + 2 \cdot 2))$



조건부 확률[p(y) > 0] : p(y | x) = p(X = x | Y = y) = p(x, y)/p(y) = p(y | x)/p(y) = p(x ∩ y) / p(x)
조건부 확률[변수 X와 Y가 서로 독립일 때] : p(x | y) = p(x)p(y)/p(y) = p(x)

이산형 확률 변수 : p(X) = 



