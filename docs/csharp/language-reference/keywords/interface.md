---
title: "インターフェイス (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "interface_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "interface キーワード [C#]"
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# インターフェイス (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インターフェイスには、[メソッド](../../../fsharp/language-reference/members/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[イベント](../../../csharp/programming-guide/events/index.md)、または[インデクサー](../../../csharp/programming-guide/indexers/index.md)のシグネチャのみが含まれています。  インターフェイスを実装するクラスまたは構造体は、インターフェイス定義で指定されているインターフェイスのメンバーを実装する必要があります。  次の例の `ImplementationClass` クラスは、`void` を返す、パラメーターのない `SampleMethod` メソッドを実装する必要があります。  
  
 使用例を含む詳細については、「[インターフェイス](../../../visual-basic/reference/command-line-compiler/index.md)」を参照してください。  
  
## 使用例  
 [!CODE [csrefKeywordsTypes#14](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#14)]  
  
 インターフェイスは、名前空間またはクラスのメンバーであり、次のメンバーのシグネチャを含むことができます。  
  
-   [メソッド](../../../fsharp/language-reference/members/methods.md)  
  
-   [プロパティ](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [インデクサー](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [イベント](../../../csharp/language-reference/keywords/event.md)  
  
 インターフェイスは、1 つ以上の基本インターフェイスから継承できます。  
  
 基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。  
  
 インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。  明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。  
  
 インターフェイスの明示的な実装の詳細とコード例については、「[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。  
  
## 使用例  
 ここでは、インターフェイスの実装例を示します。  この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。  `IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。  
  
 [!CODE [csrefKeywordsTypes#15](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#15)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [インターフェイス](../../../visual-basic/reference/command-line-compiler/index.md)   
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)   
 [クラス](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [インターフェイス](../../../visual-basic/reference/command-line-compiler/index.md)