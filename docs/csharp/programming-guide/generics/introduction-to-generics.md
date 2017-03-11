---
title: "ジェネリックの概要 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ジェネリック [C#], ジェネリックの概要"
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# ジェネリックの概要 (C# プログラミング ガイド)
ジェネリック クラスとジェネリック メソッドは、それぞれの非ジェネリック バージョンでは実現できない形で再利用性、タイプ セーフ、および効率性を兼ね備えています。  通常、ジェネリックは、コレクションおよびコレクションに対して動作するメソッドと共に使用されます。  Version 2.0 の .NET Framework クラス ライブラリには、<xref:System.Collections.Generic> という新しい名前空間が用意されています。この名前空間には、ジェネリックベースの新しいコレクション クラスがあります。  [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 2.0 以降を対象にするすべてのアプリケーションでは、<xref:System.Collections.ArrayList> などの以前の非ジェネリック クラスの代わりに、新しいジェネリック コレクション クラスを使用することをお勧めします。  詳細については、「[.NET Framework クラス ライブラリのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)」を参照してください。  
  
 また、カスタム ジェネリック型やカスタム ジェネリック メソッドを作成して、独自の汎用ソリューションを提供したり、タイプ セーフで効率的なパターンを設計したりすることもできます。  以下のコード例は、簡単な汎用リンク リスト クラスを示しています。  通常は、独自のクラスを作成するよりも、.NET Framework クラス ライブラリに用意されている <xref:System.Collections.Generic.List%601> クラスを使用してください。この例では、通常、具体的な型を使用して、リストに格納する項目の型を示すところで、型パラメーター `T` を使用しています。  このパラメーターは、次のように使用されています。  
  
-   `AddHead` メソッドのメソッド パラメーターの型として使用されています。  
  
-   `GetNext` パブリック メソッドの戻り値の型、および入れ子にされた `Node` クラスの `Data` プロパティとして使用されています。  
  
-   入れ子になったクラスのプライベート メンバー データの型として使用されています。  
  
 T は、入れ子になった `Node` クラスで使用できることに注意してください。  `GenericList<T>` を、たとえば、`GenericList<int>` のように具体的な型でインスタンス化すると、`T` の各出現箇所は、`int` に置き換えられます。  
  
 [!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/csharp/introduction-to-generics_1.cs)]  
  
 次のコード例は、クライアント コードで `GenericList<T>` ジェネリック クラスを使用して整数のリストを作成する方法を示しています。  このコードの型引数を変更するだけで、文字列や他の任意のカスタム型のリストを生成するように簡単に修正できます。  
  
 [!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/csharp/introduction-to-generics_2.cs)]  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)