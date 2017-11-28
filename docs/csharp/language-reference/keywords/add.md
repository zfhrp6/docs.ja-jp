---
title: "add (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: add_CSharpKeyword
helpviewer_keywords: add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cab77ad5a990cf85075455e347a4b1c02645af37
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="add-c-reference"></a>add (C# リファレンス)
`add` コンテキスト キーワードは、カスタム イベント アクセサーを定義するときに使用されます。このアクセサーは、クライアント コードが[イベント](../../../csharp/language-reference/keywords/event.md)をサブスクライブするときに呼び出されます。 カスタムの `add` アクセサーを指定するときは、[remove](../../../csharp/language-reference/keywords/remove.md) アクセサーも指定する必要があります。  
  
## <a name="example"></a>例  
 次の例は、カスタムの `add` アクセサーと [remove](../../../csharp/language-reference/keywords/remove.md) アクセサーが指定されているイベントを示しています。 サンプル全体については、「[方法: インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)」を参照してください。  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 通常は、独自のカスタム イベント アクセサーを提供する必要はありません。 イベントを宣言するときにコンパイラで自動生成されるアクセサーは、ほとんどのシナリオで利用することができます。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../csharp/programming-guide/events/index.md)
