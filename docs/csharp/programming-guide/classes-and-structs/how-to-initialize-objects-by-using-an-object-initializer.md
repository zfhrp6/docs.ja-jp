---
title: "方法: オブジェクト初期化子を使用してオブジェクトを初期化する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "オブジェクト初期化子 [C#], 使い方"
  - "オブジェクト [C#], 初期化"
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# 方法: オブジェクト初期化子を使用してオブジェクトを初期化する (C# プログラミング ガイド)
オブジェクト初期化子を使用すると、型のコンストラクターを明示的に呼び出さずに、宣言的な方法で型オブジェクトを初期化できます。  
  
 指定したオブジェクトでオブジェクト初期化子を使用する方法を次の例に示します。  コンパイラは、最初に既定のインスタンス コンストラクターにアクセスおよびメンバーの初期化を処理することで、オブジェクト初期化子を処理します。  したがって、クラスで既定のコンストラクターが `private` として宣言されている場合、パブリック アクセスを必要とするオブジェクト初期化子は失敗します。  
  
 匿名型を定義するオブジェクト初期化子を使用する必要があります。  詳細については、「[方法 : クエリで要素のプロパティのサブセットを返す](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)」を参照してください。  
  
## 使用例  
 オブジェクト初期化子を使用して、新しい `StudentName` 型を初期化する方法を次の例に示します。  
  
 [!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## 使用例  
 コレクション初期化子を使用して、`StudentName` 型のコレクションを初期化する方法を次の例に示します。  コレクション初期化子は、コンマで区切られた一連のオブジェクト初期化子です。  
  
 [!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## コードのコンパイル  
 このコードを実行するには、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で作成した Visual C\# コンソール アプリケーション プロジェクトに、クラスをコピーして貼り付けます。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)