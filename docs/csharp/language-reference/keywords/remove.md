---
title: "remove (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "remove_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "remove イベント アクセサー [C#]"
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# remove (C# リファレンス)
`remove` コンテキスト キーワードを使用して、クライアント コードが[イベント](../../../csharp/language-reference/keywords/event.md)へのサブスクリプションを解除したときに呼び出されるカスタム イベント アクセサーを定義できます。  カスタムの `remove` アクセサーを指定するときは、[add](../../../csharp/language-reference/keywords/add.md) アクセサーも指定する必要があります。  
  
## 使用例  
 次の例は、カスタムの [add](../../../csharp/language-reference/keywords/add.md) アクセサーと `remove` アクセサーが指定されているイベントを示しています。  サンプル全体については、「[方法 : インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)」を参照してください。  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 通常は、独自のカスタム イベント アクセサーを提供する必要はありません。  大部分のシナリオでは、イベントを宣言するときにコンパイラによって自動的に生成されるアクセサーで十分です。  
  
## 参照  
 [イベント](../../../csharp/programming-guide/events/index.md)