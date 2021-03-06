---
emoji: ๐พ
title: save, load
date: '2021-02-25 11:32:00'
author: jonghyun
tags: unity
categories: unity
---

### ์ฐธ๊ณ 

-   [\[Unity Document\] PlayerPrefs](https://docs.unity3d.com/kr/530/ScriptReference/PlayerPrefs.html)
-   [\[Unity Q&A\] How do I save a custom class of variables to playerprefs?](https://answers.unity.com/questions/610893/how-do-i-save-a-custom-class-of-variables-to-playe.html)

## Save, Load

์ ๋ํฐ ๊ฒ์์์ ์ด๋ค ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ๊ณ  ๋ถ๋ฌ์ค๋ ์ฌ๋ฌ ๋ฐฉ๋ฒ์ ์์๋ดค๋ค.

### 1\. PlayerPrefs (์ ๋ํฐ ๋ด์ฅ ํจ์)

[PlayerPrefs](https://docs.unity3d.com/kr/530/ScriptReference/PlayerPrefs.html)๋ UnityEngine ํด๋์ค ์์ ๊ตฌํ๋ ํด๋์ค๋ก ๊ฒ์ ์ธ์์ด ์งํ๋๋ ์์ค์ ๋ฐ์ดํฐ๋ฅผ ํ์ผ๋ก ์ ์ฅํ๊ฑฐ๋ ๋ถ๋ฌ์จ๋ค.

ํ์ผ์ด ์ ์ฅ๋๋ ๋ํดํธ ๊ฒฝ๋ก๋ ๋ค์๊ณผ ๊ฐ๋ค.

| macOS  | ~/Library/Preferences/unity.\[company name\].\[product name\].plist |
| ------ | ------------------------------------------------------------ |
| Window | HKCU\\Software\[company name\]\[product name\] key           |
| Linux  | ~/.config/unity3d/\[CompanyName\]/\[ProductName\]            |

PlayerPrefs๋ **Build Setting์์ ์ค์ ํ company name๊ณผ product name์ ๊ฐ์ ธ์ ๊ฒฝ๋ก์ ์ฌ์ฉ**ํ๋ค. ๋๋ถ์ ๊ฒฝ๋ก์ง์ ์ ์ ๊ฒฝ์ ์ฐ์ง ์์๋ ๋๋ค.

PlayerPrefs๋ก ๋ง๋  ์ธ์ด๋ธ ๋ก๋ ์ฝ๋๋ ๋ค์๊ณผ ๊ฐ๋ค.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class PlayerPrefsExample : MonoBehaviour
{
    public Text levelText;
    public Text experienceText;
    public Text nameText;

    [SerializeField] private int _level = 0;
    [SerializeField] private float _experience = 0.0f;
    [SerializeField] private string _name = "WhoAreYou";

    public void Load()
    {
        _level = PlayerPrefs.GetInt("Level");
        _experience = PlayerPrefs.GetFloat("Experience");
        _name = PlayerPrefs.GetString("Name");

        UpdateUI();
    }

    public void Save()
    {
        PlayerPrefs.SetInt("Level", _level);
        PlayerPrefs.SetFloat("Experience", _experience);
        PlayerPrefs.SetString("Name", _name);
    }

    private void UpdateUI()
    {
        levelText.text = _level.ToString();
        experienceText.text = _experience.ToString();
        nameText.text = _name;
    }

    private void Start()
    {
        UpdateUI();
    }
}
```

์ฝ๋๋ฅผ ๋ณด์ด๋ฏ, PlayerPrefs๋ ๋ณ์๋ง๋ค ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ๊ณ  ๊ทธ ํ์๋ int, float, string์ผ๋ก ์ ํ๋์ด ์๋ค.

#### ์ ๋ฆฌ

PlayerPrefs

-   ์ฅ์ 
    -   ์ฌ์ฉํ๊ธฐ ์์ฃผ ํธ๋ฆฌํ๋ค.
    -   ๊ฒฝ๋ก ์ง์ ์ ์ ๊ฒฝ์ฐ์ง ์์๋ ๋๋ค
-   ๋จ์ 
    -   ์ ์ฅํ  ์ ์๋ ํ์์ด ์ ํ์ ์ด๋ค. (=๊ตฌ์กฐ์ฒด๋ฅผ ์ ์ฅํ  ์ ์๋ค.)

### 2\. Custom Serializer

์ธ์ด๋ธ, ๋ก๋๋ ๊ฒฐ๊ตญ ํ์ผ๋ก ์ ์ฅํ๊ณ  ๋ถ๋ฌ์ค๋ ๊ฒ์ด๋ค. ์ฆ, Save๋ bytearray๋ก serializeํ๋ ๊ฒ์ด๊ณ  Load๋ deserializeํด์ bytearray๋ก ๋ง๋๋ ๊ฒ์ด๋ค. ์ด ์ผ์ ํ  ์ ์๋ Serializer๋ฅผ C# ๋ด์ฅ ํจ์๋ฅผ ํตํด ๊ตฌํํ  ์ ์๋ค.

```csharp
 // ์ถ์ฒ: https://answers.unity.com/questions/610893/how-do-i-save-a-custom-class-of-variables-to-playe.html 
 using System;
 using System.IO;
 using UnityEngine;
 using System.Collections;
 using System.Collections.Generic;
 using System.Runtime.Serialization.Formatters.Binary;

 public class Serializer
 {
     public static T Load<T>(string filename) where T: class
     {
         if (File.Exists(filename))
         {
             try
             {
                 using (Stream stream = File.OpenRead(filename))
                 {
                     BinaryFormatter formatter = new BinaryFormatter();
                     return formatter.Deserialize(stream) as T;
                 }
             }
             catch (Exception e)
             {
                 Debug.Log(e.Message);
             }
         }
         return default(T);
     }

     public static void Save<T>(string filename, T data) where T: class
     {
         using (Stream stream = File.OpenWrite(filename))
         {    
             BinaryFormatter formatter = new BinaryFormatter();
             formatter.Serialize(stream, data);
         }
     }
 }

 // ์ฌ์ฉ๋ฐฉ๋ฒ
 Serializer.Save<ExampleClass>(filenameWithExtension, exampleClass);
 ExampleClass exampleClass = Serializer.Load<ExampleClass>(filenameWithExtension));
```

์ด๋ ๊ฒ ํ๋ฉด ์ด๋ค ํ์์ด๋ ์ง ์ ์ฅํ  ์ ์๋ค. ํ์ง๋ง ์ง์  ๊ตฌํํด์ผ ํ  ๋ฟ๋ง ์๋๋ผ filename์ path๋ฅผ ์ง์ ํด์ ๋ฃ์ด์ค์ผ ํ๋ค๋ ๋จ์ ์ด ์๋ค.

#### ์ ๋ฆฌ

Custom Serializer

-   ์ฅ์ 
    -   ์ด๋ค ํ์์ด๋ ์ง ์ ์ฅํ  ์ ์๋ค.
-   ๋จ์ 
    -   ์ง์  ๊ตฌํํด์ผ ํ๋ค.
    -   ์ ์ฅ๊ฒฝ๋ก์ ์ ๊ฒฝ์จ์ค์ผ ํ๋ค. ์ด ๊ณผ์ ์์ ํ๋์ฝ๋ฉ์ด ๋  ์ฌ์ง๊ฐ ์๋ค.
        -   ์ด๋ ์ ๋ํฐ ๋ด๋ถ ํจ์๋ก ๋์ ์ธ ์ ์ฅ๊ฒฝ๋ก๋ฅผ ์ฌ์ฉํ๋ฉด ํด๊ฒฐํ  ์ ์๋ค.

```toc

```

