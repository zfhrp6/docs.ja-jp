---
title: "方法: グローバル名前空間エイリアスを使用する (C# プログラミング ガイド) | Microsoft Docs"
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
  - "エイリアス [C#]"
  - "グローバル名前空間 [C#]"
  - "名前空間 [C#], グローバル名前空間修飾子 [C#]"
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: グローバル名前空間エイリアスを使用する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

グローバル[名前空間](../../../csharp/language-reference/keywords/namespace.md)のメンバーにアクセスできると、そのメンバーが同名の別のエンティティによって隠される可能性がある場合に役立ちます。  
  
 たとえば、次のコードでは、`Console` は、<xref:System> 名前空間の `Console` 型ではなく、`TestApp.Console` に解決されます。  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 `System.Console` を使用すると、`System` 名前空間が `TestApp.System` クラスによって隠されているため、依然としてエラーになります。  
  
 [!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 ただし、次のように `global::System.Console` を使用すると、このエラーを回避できます。  
  
 [!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 左の識別子が `global` の場合、右の識別子の検索はグローバル名前空間から開始されます。  たとえば、次の宣言は、グローバル空間のメンバーとして `TestApp` を参照します。  
  
 [!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 `System` という名前の独自の名前空間を作成することはお勧めしません。そのようなコードに遭遇することはほとんどありません。  ただし、大型のプロジェクトでは、フォームによっては名前空間の重複が実際に発生する可能性があります。  そのような場合は、グローバル名前空間修飾子によって、ルート名前空間を指定できます。  
  
## 使用例  
 次の例では、`System` 名前空間を使用して `TestClass` クラスを格納しています。そのため、`System` 名前空間によって隠されている `System.Console` クラスを参照するために `global::System.Console` を使用する必要があります。  また、`System.Collections` 名前空間を参照するのに `colAlias` エイリアスを使用するため、名前空間の代わりにこのエイリアスを使用して <xref:System.Collections.Hashtable?displayProperty=fullName> のインスタンスを作成しています。  
  
 [!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
  **A 1**  
**B 2**  
**C 3**   
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)   
 [. 演算子](../../../csharp/language-reference/operators/member-access-operator.md)   
 [:: 演算子](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)