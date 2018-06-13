---
title: Null 許容型のボックス化 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334757"
---
# <a name="boxing-nullable-types-c-programming-guide"></a>Null 許容型のボックス化 (C# プログラミング ガイド)
Null 許容型に基づくオブジェクトは、オブジェクトが Null 以外の場合にのみボックス化されます。 <xref:System.Nullable%601.HasValue%2A> が `false` の場合、オブジェクト参照はボックス化ではなく `null` に割り当てられます。 例:  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 オブジェクトが Null 以外の場合 (<xref:System.Nullable%601.HasValue%2A> が `true` の場合)、ボックス化が発生しますが、Null 許容型オブジェクトの基礎になっている基本型のみがボックス化されます。 Null 以外の Null 許容値型をボックス化すると、値の型をラップする <xref:System.Nullable%601?displayProperty=nameWithType> ではなく、値の型自体がボックス化されます。 例:  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 ボックス化された 2 つのオブジェクトは、Null 非許容の型のボックス化で作成されたオブジェクトと同じになります。 また、Null 非許容のボックス化された型と同様に、次の例のように、Null 許容型にボックス化を解除できます。  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>コメント  
 ボックス化されるとき、Null 許容型の動作には 2 つの利点があります。  
  
1.  Null 許容型オブジェクトとそれがボックス化されたものは null かどうかをテストできます。  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  ボックス化された Null 許容型はその基礎型の機能を完全サポートします。  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
 [方法: Null 許容型を識別する](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
