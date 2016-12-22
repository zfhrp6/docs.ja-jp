---
title: "namespace (C# リファレンス) | Microsoft Docs"
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
  - "namespace_CSharpKeyword"
  - "namespace"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "名前空間キーワード [C#]"
  - "スコープ [C#]"
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# namespace (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`namespace` のキーワードは、関連するオブジェクトを含む範囲を宣言するために使用されます。  コード要素を整理およびグローバルに一意の型を作成するには、名前空間を使用できます。  
  
 [!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## 解説  
 名前空間内では、以下の型を 1 つ以上宣言できます。  
  
-   別の名前空間  
  
-   [クラス](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 C\# ソース ファイル内に名前空間を明示的に宣言しているかどうかに関係なく、コンパイラは既定の名前空間を追加します。  作成される無名の名前空間は、グローバル名前空間とも呼ばれ、すべてのファイルに存在します。  グローバル名前空間内にある識別子は、名前付き名前空間で利用できます。  
  
 名前空間は、暗黙的にパブリックにアクセスされます。この属性は変更できません。  名前空間内の要素に割り当てることができるアクセス修飾子については、「[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)」を参照してください。  
  
 名前空間は、2 つ以上の宣言で定義できます。  たとえば、次の例では、`MyCompany` 名前空間の一部として 2 つのクラスを定義しています。  
  
 [!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## 使用例  
 入れ子になった名前空間で静的なメソッドを呼び出す方法の例を次に示します。  
  
 [!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## 参照項目  
 名前空間の使用方法の詳細については、次のトピックを参照してください。  
  
-   [名前空間](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [使用](../../../csharp/language-reference/keywords/using.md)