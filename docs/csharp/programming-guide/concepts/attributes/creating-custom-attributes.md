---
title: "カスタム属性の作成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b71bf8fe1f4d448bf373fcab4bccd89bca4672b8
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-c"></a>カスタム属性の作成 (C#)
属性クラスを定義することで、独自のカスタム属性を作成できます。属性クラスは、<xref:System.Attribute> の直接的または間接的な派生クラスです。これにより、メタデータの中で属性の定義をすばやく簡単に特定できます。 型にそれを記述したプログラマーの名前でタグを付けるとします。 `Author` というカスタム属性クラスを定義します。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 クラス名は属性の名前の `Author` です。 このクラスは `System.Attribute` から派生しているので、カスタム属性クラスです。 コンストラクターのパラメーターはカスタム属性の位置指定パラメーターです。 この例では、`name` が位置指定パラメーターになります。 パブリックな読み取り/書き込みフィールドまたはプロパティは名前付きパラメーターです。 この場合は、`version` が唯一の名前付きパラメーターです。 `AttributeUsage` 属性を使用して、クラスと `struct` の宣言に対してのみ `Author` 属性を有効にしていることに注意してください。  
  
 この新しい属性の使用方法は次のとおりです。  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` には名前付きパラメーター `AllowMultiple` があります。これを使用すると、カスタム属性が 1 回しか指定できない属性か、または複数回指定できる属性かを設定できます。 次のコード例では、複数回指定できる属性が作成されます。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 次のコード例では、同じ型の複数の属性が 1 つのクラスに適用されます。  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  属性クラスにプロパティが含まれている場合、そのプロパティは読み取り/書き込み可能である必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection>   
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)   
 [カスタム属性の記述](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [属性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
