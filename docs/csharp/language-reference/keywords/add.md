---
title: "add (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "add_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "add イベント アクセサー [C#]"
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# add (C# リファレンス)
`add` コンテキスト キーワードを使用して、クライアント コードが[イベント](../../../csharp/language-reference/keywords/event.md)にサブスクライブしたときに呼び出されるカスタム イベント アクセサーを定義できます。  カスタムの `add` アクセサーを指定するときは、[remove](../../../csharp/language-reference/keywords/remove.md) アクセサーも指定する必要があります。  
  
## 使用例  
 次の例は、カスタムの `add` アクセサーと [remove](../../../csharp/language-reference/keywords/remove.md) アクセサーが指定されているイベントを示しています。  サンプル全体については、「[方法 : インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)」を参照してください。  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/csharp/add_1.cs)]  
  
 通常は、独自のカスタム イベント アクセサーを提供する必要はありません。  大部分のシナリオでは、イベントを宣言するときにコンパイラによって自動的に生成されるアクセサーで十分です。  
  
## 参照  
 [イベント](../../../csharp/programming-guide/events/index.md)