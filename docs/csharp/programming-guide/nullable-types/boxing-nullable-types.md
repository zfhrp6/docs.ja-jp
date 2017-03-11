---
title: "Null 許容型のボックス化 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ボックス化 [C#], null 許容型"
  - "null 許容型 [C#], ボックス化とボックス化解除"
  - "ボックス化解除 [C#], null 許容型"
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# Null 許容型のボックス化 (C# プログラミング ガイド)
null 許容型に基づくオブジェクトは、null 以外の場合にのみボックス化されます。  <xref:System.Nullable%601.HasValue%2A> が `false` の場合は、ボックス化ではなく、オブジェクト参照が `null` に代入されます。  次に例を示します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 オブジェクトが null 以外の場合 \(<xref:System.Nullable%601.HasValue%2A> が `true` の場合\)、ボックス化が実行されますが、null 許容オブジェクトの基になる型のみがボックス化されます。  null 以外の null 許容値型のボックス化では、その値型自体がボックス化され、その値型をラップする <xref:System.Nullable%601?displayProperty=fullName> はボックス化されません。  次に例を示します。  
  
```  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 上の例のボックス化された 2 つのオブジェクトは、null 非許容型のボックス化によって作成されたオブジェクトと同じです。  また、ボックス化された null 非許容型と同様に、null 許容型にボックス化解除できます。この例を次に示します。  
  
```  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## 解説  
 ボックス化された場合の null 許容型の動作には、次の 2 つの利点があります。  
  
1.  null 許容オブジェクトとそのボックス化されたオブジェクトは、次のように null であるかどうかをテストできます。  
  
    ```  
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
  
2.  ボックス化された null 許容型は、次のように基になる型の機能を完全にサポートします。  
  
    ```  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [方法: Null 許容型を識別する](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)