---
emoji: π£
title: Addressable Asset System
date: '2021-03-02 15:39:00'
author: jonghyun
tags: unity
categories: unity
---
## κΈ°μ‘΄ μμ μμ€νμ μ₯λ¨μ 

1.  μ§μ  λ νΌλ°μ€
    -   μ₯μ 
        -   μ½κ³  μ½λ κΈΈμ΄κ° μ€μ΄λ λ€.
    -   λ¨μ 
        -   μ€μ λ‘ μ°μ§ μμλ λ©λͺ¨λ¦¬κ° μ¬λΌκ° μλ€.
2.  λ¦¬μμ€ ν΄λ
    -   μ₯μ 
        -   μ½κ³  νΈλ¦¬νλ€
    -   λ¨μ 
        -   λΉλν  λ, λ¦¬μμ€ ν΄λ μμ νμΌμ κ° νμΌλ§λ€ λΉλνλ―λ‘ λΉλ μ¬μ΄μ¦κ° μ»€μ§λ€.
        -   κ²μ μμ μ λ¦¬μμ€ νμΌμ λν μΈλ±μ±μ νλ€λ³΄λ μ± μμ μκ°μ΄ κΈΈμ΄μ§λ€.
        -   λ¦¬μμ€ν΄λ μμ μ κ·Όν  λλ νμΌ μ΄λ¦μ μ€νΈλ§μΌλ‘ κ°μ§κ³  μκΈ° λλ¬Έμ μμμ μ΄λ¦μ λ³κ²½ν  μκ° μλ€.
    -   κ²°λ‘ 
        -   μ¬μ©ν  λ, κ²½κ³ν΄μΌ νλ€.
3.  μμ λ²λ€
    -   μ₯μ 
        -   λΉλ μ¬μ΄μ¦ μ κ°
        -   μ± μμ μκ°μ΄ μ§§λ€
    -   λ¨μ 
        -   μμλ²λ€ μ’μμ±(depedency), λ²μ  κ΄λ¦¬λ‘ μΈν΄ μ¬μ©νκΈ° κΉλ€λ‘­λ€.
        -   λͺ¨λ  κ²μ΄ μ½λλ‘ λμ΄ μμ΄μ μλν° μμ€μμ μμμ΄ κ±°μ μλ€.

### κΈ°μ‘΄ μμ μμ€νμ μν¬ νλ‘

λ³΄ν΅ **μ§μ  λ νΌλ°μ€ -> λ¦¬μμ€ ν΄λ -> μμλ²λ€**μ μμλ‘ κ°λ°μ΄ μ§νλκ³ , μ΄λ° κ²½μ° μ½λ λ³κ²½μ΄ νμλ€.

## Addressable Asset System

### Addressable Asset?

-   Addressκ° ν λΉλ μμ. μ΄ Addressλ‘ μμμ μ κ·Όν  μ μλ€.
-   Addressable Asset System = Asset **κ΄λ¦¬ + λ‘λ© + λΉλ**

### μ₯μ 

-   μμ λΉλμ λ°°ν¬μ λ¨μν
-   μμ κ΄λ¦¬ μ©μ΄
-   μ½λ λ³κ²½ X

### κ΅¬ν

1.  ν¨ν€μ§ λ§€λμ μμ Addressables System μ μ©
2.  Inspectorμμ ν΄λΉ μμμ ν΄λ¦­νκ³  Addressableμ μ²΄ν¬ (ν΄λΉ λ΄μ©μ Addressable μλμ°μμ νμΈ κ°λ₯)
3.  "μ΄λλ μ€"λ₯Ό μ΄μ©ν Loading, Instantiating
	
	```cs 
	GameObject myGameObj; //// λ‘λ©μ νκ³ , λ‘λ©μ΄ λλλ©΄ λ°λμν¬ ν¨μλ₯Ό κ΅¬λν΄λμ μ μλ€.
	Addressables.LoadAsset<GameObject>("AssetAddress").Completed += onLoadDone; } //// λ‘λ©μ΄ λλλ©΄ λ°λνλ μ½λ°± ν¨μ
	private void onLoadDone(IAsyncOperation<Sprite> obj) { myGameObject = obj.Result; }
	Instantiating Addressbles.Instantiate<GameObject>("AssetAddress"); // "AssetReference"λ₯Ό μ΄μ©ν λ‘λ©κ³Ό Instantiating 
	// - Inspectorμμ Address μλ ₯μ λμμ€λ€.
	// - μ§μ  νμ΄νμ΄ μμ΄ μ€ν λ°μμ΄ μλ€.
	public AssetReference spawnObject; public void Spawn() {
		spawnObject.InstantiateAsync();
		spawnObject.LoadAsset<GameObject>();
		spawnObject.Instantiate<GameObject>(pos, rot);
	}
	```

5.  μ΄λλ μ€ ν΄μ 

    -   LoadAsset => ReleaseAsset()
    -   Instantiate() => ReleaseInstance()

    ```csharp
    Addressables.ReleaseAsset<GameObject>(obj);
    Addressables.ReleaseInstance<GameObject>(obj, delay);

    AddRef.ReleaseAsset<GameObject>(obj);
    AddRef.ReleaseInstace<GameObject>(obj);
    ```


### μλ λ°©μ

-   Addressableμ ν¬κ² '**μ΄κΈ°ν**'μ '**λ‘λ**'μΌ λ μλνλ€.
-   λ΄λΆ νμΈ λ λ¦¬μμ€μ μ΄λλ μ€λ₯Ό κ΄λ¦¬νλ 'Addressables'κ³Ό μ€μ  νμΌμ κ΄λ¦¬νλ 'Resource Manager'κ° μλ€.
-   μ΄κΈ°ν
    -   Addressble
        -   Content Catalogλ₯Ό μ°Έκ³ ν΄ μ€μ  λ¦¬μμ€ μμΉλ₯Ό λ΄λ Resource Locatorλ₯Ό νμ±νλ€.
        -   Content Catalog = μ£Όμ μ λ³΄λ₯Ό Serializationν΄μ JSONνμΌ ννλ‘ κ°μ§κ³  μλ€.
    -   Resource Manager
        -   Providerλ₯Ό λ±λ‘νλ€.
        -   Provider = κ° νμΌ νμμ λ°λΌ μ΅μ νλ λ‘λ λ°©μμ κ°μ§κ³  μλ€.
-   λ‘λ
    1.  μ¬μ©μκ° μ½λλ‘ λ‘λλ₯Ό μμνλ€. μ΄ λ, Addressablesμ μ£Όμλ₯Ό λκ²¨μ€λ€.
    2.  Addressablesμ Resource Locatorκ° μ€μ  λ¦¬μμ€ μμΉλ₯Ό Resource Managerμκ² λκΈ΄λ€.
    3.  Resource Managerλ μ€μ  λ¦¬μμ€λ₯Ό λ³΄κ³  μ μ ν Providerλ₯Ό μ μ ν΄μ AsyncOperationμ λ°ννλ€.
    4.  λ‘λκ° λ€ λλ©΄ λ‘λ μλ£ μ΄λ²€νΈκ° λ°λνλ€.

```toc

```
