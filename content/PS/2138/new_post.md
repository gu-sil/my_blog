---
emoji:π‘
title:μ κ΅¬μ μ€μμΉ
date:'2021-11-13 23:45:37'
author:hyun
tags:bruteforce
categories:PS
---

### μΆμ²

[https://www.acmicpc.net/problem/2138](https://www.acmicpc.net/problem/2138)

### λ¬Έμ 

Nκ°μ μ€μμΉμ Nκ°μ μ κ΅¬κ° μλ€. κ°κ°μ μ κ΅¬λ μΌμ Έ μλ μνμ κΊΌμ Έ μλ μν μ€ νλμ μνλ₯Ό κ°μ§λ€. i(1 < i < N)λ² μ€μμΉλ₯Ό λλ₯΄λ©΄ i-1, i, i+1μ μΈ κ°μ μ κ΅¬μ μνκ° λ°λλ€. μ¦, κΊΌμ Έ μλ μ κ΅¬λ μΌμ§κ³ , μΌμ Έ μλ μ κ΅¬λ κΊΌμ§κ² λλ€. 1λ² μ€μμΉλ₯Ό λλ μ κ²½μ°μλ 1, 2λ² μ κ΅¬μ μνκ° λ°λκ³ , Nλ² μ€μμΉλ₯Ό λλ μ κ²½μ°μλ N-1, Nλ² μ κ΅¬μ μνκ° λ°λλ€.

Nκ°μ μ κ΅¬λ€μ νμ¬ μνμ μ°λ¦¬κ° λ§λ€κ³ μ νλ μνκ° μ£Όμ΄μ‘μ λ, κ·Έ μνλ₯Ό λ§λ€κΈ° μν΄ μ€μμΉλ₯Ό μ΅μ λͺ λ² λλ₯΄λ©΄ λλμ§ μμλ΄λ νλ‘κ·Έλ¨μ μμ±νμμ€.

### μλ ₯

μ²«μ§Έ μ€μ μμ°μ N(2 β€ N β€ 100,000)μ΄ μ£Όμ΄μ§λ€. λ€μ μ€μλ μ κ΅¬λ€μ νμ¬ μνλ₯Ό λνλ΄λ μ«μ Nκ°κ° κ³΅λ°± μμ΄ μ£Όμ΄μ§λ€. κ·Έ λ€μ μ€μλ μ°λ¦¬κ° λ§λ€κ³ μ νλ μ κ΅¬λ€μ μνλ₯Ό λνλ΄λ μ«μ Nκ°κ° κ³΅λ°± μμ΄ μ£Όμ΄μ§λ€. 0μ μΌμ Έ μλ μν, 1μ κΊΌμ Έ μλ μνλ₯Ό μλ―Ένλ€.

### μΆλ ₯

μ²«μ§Έ μ€μ λ΅μ μΆλ ₯νλ€. λΆκ°λ₯ν κ²½μ°μλ -1μ μΆλ ₯νλ€.

μμ  μλ ₯ 1

```
3
000
010
```

μμ  μΆλ ₯ 1

`3`

### μ κ·Ό 1 - λΈλ£¨νΈν¬μ€

κ°μ₯ κ°λ¨νκ² λͺ¨λ  κ²½μ°μ μλ₯Ό λ€ν΄λ³΄λ κ²μ ν΄λ³Ό μ μλ€. μ΄ κ²½μ°μ λΆκ°λ₯ν κ²½μ°λ μμ£Ό μ½κ² νλ³ν  μ μλ€. μλν΄λ³΄κΈ° μ μ λ³΅μ‘λλ₯Ό μκ°ν΄λ³΄μ. μ κ΅¬μ κ°μλ μ΅λ 100,000κ°μ΄λ€. μ¦, λͺ¨λ  κ²½μ°μ μλ 2^100000μ΄λ€. νλ μλ€.

### μ κ·Ό 2 - μ΅μ ν 1

λ°λ‘ λͺ¨λ  κ²½μ°λ₯Ό ν΄λ³Ό μλ μλ€. κ·Έλ λ€λ©΄ μ΅μ νλ₯Ό ν΄λ³Ό μ μμ§ μμκΉ? λ¨Όμ , νλμ μ κ΅¬λ§ μκ°ν΄λ³΄μ. μ΄ λ, μ£Όλͺ©ν  μ μλκ±΄ μ€μμΉλ₯Ό νλ² λλ₯Ό λ λ°λλ κ±΄, ν΄λΉ μ€μμΉμ μμΉμ μμμ΄λ€. κ·Έλ λ€λ©΄, Nλ²μ§Έ μ κ΅¬μ μμ₯μμ κ²½μ°μ μλ λ€μκ³Ό κ°λ€.

κ²°κ³Όμ Nλ²μ§Έ μ κ΅¬μ μνμ λ€λ¦ β N-1, N, N+1 λ²μ§Έμ μ€μμΉ μ€ 1κ° λλ 3κ°κ° λλ Έλ€.

κ°μ β N-1, N, N+1 λ²μ§Έ μ€μμΉ μ€ μλ¬΄κ²λ λλ¦¬μ§ μμκ±°λ 2κ°κ° λλ Έλ€.

Nλ²μ§Έλ‘ λ³΄λ λ°©λ²μ λλ¬΄ λ§μ κ²½μ°μ μλ₯Ό λ³λλ€. μ΄ λ°©λ²λ λλ¬΄ λ³΅μ‘ν΄μ§λ―λ‘ λ€λ₯Έ λ°©λ²μ μκ°ν΄λ΄μΌκ² λ€.

### μ κ·Ό 3 - μ΅μ ν 2

μμκ° μκ΄μλ λ¬Έμ λ₯Ό μ½κ² νΈλ λ°©λ² μ€ νλλ μμλ₯Ό κ°μ λ‘ λ§€κΈ°λ κ²μ΄λ€. μ²«λ²μ§Έ μ κ΅¬λ₯Ό λ³΄μ. μ²«λ²μ§Έ μ κ΅¬μ μν₯μ μ€ μ μλ κ±΄, μ²«λ²μ§Έμ λλ²μ§Έ μ€μμΉλΏμ΄λΌμ κ²½μ°μ μκ° λͺκ° μλ€. κ΅¬μ²΄μ μΌλ‘ λμ΄ν΄λ³΄λ©΄,

μνκ° κ°μ

1. μ²«λ²μ§Έμ λλ²μ§Έ μ€μμΉλ₯Ό μ λΆ λλ λ€.
2. μ²«λ²μ§Έμ λλ²μ§Έ μ€μμΉ λͺ¨λ λλ₯΄μ§ μμλ€.

λ€λ¦

1. μ²«λ²μ§Έ μ€μμΉλ₯Ό λλ λ€.
2. λλ²μ§Έ μ€μμΉλ₯Ό λλ λ€.

κ·Έλ¬λ©΄ λκ°μ μ κ΅¬μ μνκ° λκ°μ κ²½μ°μ μλ‘ λλ μ§λ€.

κ·ΈλΌ μΈλ²μ§Έ μ κ΅¬μ κ²½μ°λ₯Ό λ³΄μ. μ¬κΈ°μ  μμ λ₯Ό μλ‘ λ€κ² λ€.

μμ μμ  μ²«λ²μ§Έ μ κ΅¬κ° κΊΌμ ΈμμΌλκΉ, λ¨Όμ  κΊΌμ§ 1μ κ²½μ°λ₯Ό λ³Έλ€. λλ€ λλ Έλ€λ©΄ μΈλ²μ§Έ μ κ΅¬λ λλ²μ§Έ μ€μμΉλ₯Ό ν΅ν΄μ μΌμ§ μνλ€. **κ·Έλ°λ° μ¬μ€ μΈλ²μ§Έ μ κ΅¬μ μνλ₯Ό μ€μνκ² μλλ€.** μ€μνκ±΄ λλ²μ§Έ μ κ΅¬μ μνλ€. μλνλ©΄ `λλ²μ§Έ μ€μμΉμ μνκΉμ§ μ ν΄μ§ μν©μ΄κΈ° λλ¬Έμ λλ²μ§Έ μ κ΅¬μ μνλ μΈλ²μ§Έ μ€μμΉκ° κ²°μ νκΈ° λλ¬Έμ΄λ€.`

κΊΌμ§ 1λ²μ κ²½μ°μ μ²«λ²μ§Έμ λλ²μ§Έ μ€μμΉλ₯Ό μ λΆ λλ μΌλ λλ²μ§Έ μ κ΅¬λ κΊΌμ§ μνλ€. κ·Έλ¬λ―λ‘ μΈλ²μ§Έ μ€μμΉλ λ¬΄μ‘°κ±΄ λλ¬μΌ νλ€.

μ¦, μ΄μ λΆν° λΆκΈ°λ λλ μ§μ§ μλλ€. κ·Έλ λ€λ©΄ μκ° λ³΅μ‘λλ O(2N) = O(N)μΌλ‘ κ·κ²°λλ€. κ½€ λΉ λ₯΄λ€.

κ΅¬ν
```
#include <iostream>
#include <string>
#include <cmath>
#define MAX_SIZE 100000
#define INF 1234567890;
using namespace std;

bool bulbs[MAX_SIZE];
bool ans[MAX_SIZE];
int N;

// nλ²μ§Έ μ€μμΉλ₯Ό λλ₯Έλ€.
void click_switch(int n)
{
	for (int i = n-1; i <= n+1; ++i)
	{
		if (i < 0 || i >= MAX_SIZE) continue;
		bulbs[i] = !bulbs[i];
	}
}

// nλ²μ§ΈκΉμ§ λ΅κ³Ό κ°μμ§ νμΈνλ€.
bool is_answer(int n)
{
	for (int i = 0; i < n; ++i)
	{
		if (bulbs[i] != ans[i]) return false;
	}
	return true;
}

// indexλ²μ§Έ μ κ΅¬μ μνλ₯Ό κ²°μ νλ€.
// λ§μ§λ§λ²μ§ΈλΌλ©΄ μμ μ μνλ₯Ό κ²°μ νκ³  λ΅μΈμ§ κ²μ¬ν΄μ λ§μΌλ©΄ clickλ₯Ό λ°ννλ€.
int solve(int index, int clicked)
{
	int res;
	bool has_clicked = false;

	// N == 2μΌ λ, νΉλ³ μ²λ¦¬
	if (index >= N) return is_answer(N) ? clicked : INF;

	if (bulbs[index - 1] != ans[index - 1])
	{
		click_switch(index);
		clicked++;
		has_clicked = true;
	}

	if (index == N - 1) {// κΈ°μ μ¬λ‘
		res = is_answer(N) ? clicked : INF;
	}
	else {// μ¬κ·μ¬λ‘
		res = solve(index+1, clicked);
	}
	if (has_clicked) click_switch(index);
	return res;
}

int main()
{
	int i;
	int res = INF;

	cin >> N;
	string str;
	cin >> str;
	for (i=0;i<N;++i)
		bulbs[i] = str[i] == '1' ? true : false;
	cin >> str;
	for (i=0;i<N;++i)
		ans[i] = str[i] == '1' ? true : false;
	if (bulbs[0] == ans[0])
	{
		// 1,2λ²μ§Έ μ€μμΉλ₯Ό μ λΆ λλ₯΄μ§ μμ κ²½μ°
		res = min(res, solve(2, 0));
		// 1,2λ²μ§Έ μ€μμΉλ₯Ό μ λΆ λλ₯Έ κ²½μ°
		click_switch(0);
		click_switch(1);
		res = min(res, solve(2, 2));
	}
	else
	{
		// 1λ²μ§Έ μ€μμΉλ₯Ό λλ₯Έ κ²½μ°
		click_switch(0);
		res = min(res, solve(2, 1));
		click_switch(0);
		// 2λ²μ§Έ μ€μμΉλ₯Ό λλ₯Έ κ²½μ°
		click_switch(1);
		res = min(res, solve(2, 1));
	}
	res = res == 1234567890 ? -1 : res;
	cout << res << "\n";
	return (0);
}
```
