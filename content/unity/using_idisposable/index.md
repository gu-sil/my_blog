---
emoji: ๐
title: using, IDisposable
date: '2021-09-10 20:37:00'
author: jonghyun
tags: unity
categories: unity
---

## ์์ 

```
string manyLines=@"This is line one
This is line two
Here is line three
The penultimate line is line four
This is the final, fifth line.";

using (var reader = new StringReader(manyLines))
{
   string? item;
   do {
       item = reader.ReadLine();
       Console.WriteLine(item);
  } while(item != null);
}

// https://docs.microsoft.com/ko-kr/dotnet/csharp/language-reference/keywords/using-statement
```

## Using?

- `using` ๋ฌธ์ ๋ค๋ฅธ namespace๋ฅผ ์ฐธ๊ณ ํ๋ ค๊ณ  ํ  ๋ ์จ๋ณธ ์  ์์ ๊ฒ์ด๋ค.

- ```
  using UnityEngine;
  ```

- ์ด ๊ฒฝ์ฐ๋ง๊ณ ๋ ๋ค๋ฅธ ๋ฐฉ์์ผ๋ก using๋ฌธ์ ์ฌ์ฉํ  ์ ์๋๋ฐ, ์ด๋ namespace์๋ ์ ํ ๋ฌด๊ดํ ์ด์ ๋ค.

- using๋ฌธ์ ํน์  ์ธ์คํด์ค๋ฅผ ์์์ ์ผ๋ก ์ฌ์ฉํ๊ธฐ ์ํด ์ธ ์ ์๋ค. ์ ์์ ์์ using๋ฌธ์ ์ค๊ดํธ๊ฐ ๋๋๋ฉด reader ์ธ์คํด์ค๊ฐ ์์์ ๋ฉ๋ชจ๋ฆฌ ํด์ ๋๋ค.

- ์ด๋ฅผ ํตํด ๋ค์๊ณผ ๊ฐ์ ์ฅ์ ์ ํ๋ํ๋ค.

  1. ํด๋์ค์ ๋ผ์ดํ ์ฌ์ดํด์ ๋ชํํ ํ  ์ ์๋ค.
  2. GC ํธ์ถ์ ํ์๋ฅผ ์ค์ผ ์ ์๋ค.

- ๋ชจ๋  ๊ฐ์ฒด๋ฅผ using๋ฌธ ์กฐ๊ฑด ์์ ๋ฃ์ ์๋ ์๋ค. microsoft docs์์๋ IDisposable๋ฅผ ์์ํ๋ ๊ฐ์ฒด๋ง์ด using๋ฌธ ์์ ๋ค์ด์ฌ ์ ์๋ค๊ณ  ๋ช์ํ๋ค.

## IDisposable?

- `Disposable`์ ์ผํ์ฉ์ด๋ผ๋ ๋ป์ด๋ค.
- Dispose() ๋ฉ์๋๋ฅผ ๊ตฌํํด์ผ ํ๋ค. ์ด ๋ฉ์๋๋ using๋ฌธ์ด ๋๋๋ ์์ ์ ํธ์ถ๋๋ค.

### ์ฐธ๊ณ 

- [๋ค์ด๋ฒ ๋ธ๋ก๊ทธ | C# IDisposable](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=94cogus&logNo=221539195761)

- [๋ง์ดํฌ๋ก์ํํธ ๋ฌธ์ | using](https://docs.microsoft.com/ko-kr/dotnet/csharp/language-reference/keywords/using-statement)
- [๋ง์ดํฌ๋ก์ํํธ ๋ฌธ์ | IDisposable](https://docs.microsoft.com/ko-kr/dotnet/api/system.idisposable?view=net-5.0)
