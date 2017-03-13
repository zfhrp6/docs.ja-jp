---
title: "インターフェイスのインデクサー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アクセサー [C#], インデクサー"
  - "インデクサー [C#], インターフェイス"
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# インターフェイスのインデクサー (C# プログラミング ガイド)
[interface](../../../csharp/language-reference/keywords/interface.md) に対してインデクサーを宣言できます。  インターフェイス インデクサーのアクセサーは、[クラス](../../../csharp/language-reference/keywords/class.md)のインデクサーと次の点が異なります。  
  
-   インターフェイスのアクセサーは修飾子を使用しません。  
  
-   インターフェイスのアクセサーには本体がありません。  
  
 したがって、アクセサーの目的は、インデクサーが読み取り\/書き込み、読み取り専用、または書き込み専用のいずれであるかを示すことです。  
  
 次に示すのは、インターフェイス インデクサーのアクセサーの例です。  
  
 [!code-cs[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 インデクサーのシグネチャは、同じインターフェイスで宣言されている他のすべてのインデクサーのシグネチャとは異なるシグネチャである必要があります。  
  
## 使用例  
 次の例は、インターフェイスのインデクサーの実装方法を示しています。  
  
 [!code-cs[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 前の例では、インターフェイス メンバーの完全限定名を使うことで、明示的なインターフェイス メンバーの実装を使用できます。  次に例を示します。  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 ただし、完全限定名は、同じインデクサー シグネチャを持つ複数のインターフェイスがクラスで実装されている場合に、あいまいさを避けるためだけに必要です。  たとえば、 `Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスに同じインデクサー シグネチャがある場合は、明示的なインターフェイス メンバーの実装が必要になります。  つまり、次のインデクサー宣言では、`IEmployee` インターフェイスのインデクサーが実装されます。  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 一方、次の宣言では `ICitizen` インターフェイスのインデクサーが実装されます。  
  
```  
public string ICitizen.this   
{   
}   
```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)