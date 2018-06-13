---
title: 既定値の一覧表 (C# リファレンス)
description: 既定のコンストラクターによって返される値の型の既定値について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218791"
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
