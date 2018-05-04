---
title: 既定値の一覧表 (C# リファレンス)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a>既定値の一覧表 (C# リファレンス)

次の表では、既定のコンストラクターによって返される値型の既定値を示します。 既定のコンストラクターは、次のように `new` 演算子を使って呼び出されます。

```csharp
int myInt = new int();
```

上のステートメントは次のステートメントと同じ効果があります。

```csharp
int myInt = 0;
```

C# では初期化されていない変数を使うことができないことに注意してください。

|値の種類|既定値|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0.0D|
|[enum](enum.md)|式 (E)0 によって生成される値。E は列挙型識別子です。|
|[float](float.md)|0.0F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="see-also"></a>関連項目
 [C# リファレンス](../index.md)  
 [C# プログラミング ガイド](../../programming-guide/index.md)  
 [値型の一覧表](value-types-table.md)  
 [値型](value-types.md)  
 [組み込み型の一覧表](built-in-types-table.md)  
 [型のリファレンス表](reference-tables-for-types.md)
