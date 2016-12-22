---
title: "名前空間 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 名前空間"
  - "名前空間 [C#]"
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 名前空間 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# プログラミングでは、名前空間が 2 つの点で盛んに使用されます。  1 つは、.NET Framework では、次のように名前空間を使用して多くのクラスを編成します。  
  
 [!code-cs[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` が名前空間で、`Console` がこの名前空間のクラスです。  `using` キーワードを使用すると、次の例のように完全な名前を記述する必要がなくなります。  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-cs[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 詳細については、「[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)」を参照してください。  
  
 もう 1 つは、独自の名前空間を宣言すると、大型のプログラミング プロジェクトでクラス名とメソッド名のスコープの管理が容易になります。  次の例に示すように、[namespace](../../../csharp/language-reference/keywords/namespace.md) キーワードを使用して名前空間を宣言します。  
  
 [!code-cs[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## 名前空間の概要  
 名前空間には、次の特徴があります。  
  
-   名前空間を使用することにより、大型のコード プロジェクトを整理できます。  
  
-   名前空間は、`.` 演算子を使って区切ります。  
  
-   `using directive`を使用すると、クラスごとに名前空間の名前を指定する必要がなくなります。  
  
-   `global` 名前空間は "ルート" 名前空間です。`global::System` は、常に .NET Framework 名前空間の `System` を参照します。  
  
## 関連項目  
 名前空間の詳細については、次のトピックを参照してください。  
  
-   [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [方法 : My 名前空間を使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)   
 [:: 演算子](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [. 演算子](../../../csharp/language-reference/operators/member-access-operator.md)