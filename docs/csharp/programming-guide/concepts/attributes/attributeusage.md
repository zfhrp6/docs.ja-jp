---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81e7440279a2d7dfa801394ee0e9af6181da3c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)
カスタム属性クラスの使用方法を決定します。 `AttributeUsage` は、カスタム属性の定義に適用して新しい属性の適用方法を制御できる属性です。 明示的に適用するときの既定の設定は次のようになります。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 この例では、属性にできる任意のコード エンティティに `NewAttribute` クラスを適用できますが、各エンティティに適用できるのは 1 回だけです。 基底クラスに適用すると、派生クラスによって継承されます。  
  
 `AllowMultiple` 引数と `Inherited` 引数は省略できるので、次のコードは同じ効果を持ちます。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 最初の `AttributeUsage` 引数は、<xref:System.AttributeTargets> 列挙型の 1 つまたは複数の要素でなければなりません。 次のように、複数のターゲット型を OR 演算子で 1 つにまとめることができます。  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 `AllowMultiple` 引数を `true` に設定すると、次のように、結果の属性を 1 つのエンティティに複数回適用できます。  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 この例では、`AllowMultiple` が `true` に設定されているので、`MultiUseAttr` を繰り返し適用できます。 示されているどちらの形式でも、複数の属性を適用できます。  
  
 `Inherited` を `false` に設定すると、属性化されたクラスから派生するクラスは属性を継承しません。 例:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 この例では、`Attr1` は継承によって `DClass` に適用されません。  
  
## <a name="remarks"></a>コメント  
 `AttributeUsage` 属性は、1 回だけ使用できる属性です。同じクラスに複数回適用することはできません。 `AttributeUsage` は <xref:System.AttributeUsageAttribute> の別名です。  
  
 詳しくは、「[リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例を見ると、`AttributeUsage` 属性に対する `Inherited` 引数と `AllowMultiple` 引数の効果、およびクラスに適用されているカスタム属性の列挙方法がわかります。  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a>出力例  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)  
 [属性](https://msdn.microsoft.com/library/5x6cd29c)  
 [リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [属性](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [カスタム属性の作成 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
