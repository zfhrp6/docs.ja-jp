---
title: "方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 617af10d3fb5f9371d5893b87a91a48639d44a53
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)
ここでは、マルチキャスト デリゲートを作成する例について説明します。 [デリゲート](../../../csharp/language-reference/keywords/delegate.md) オブジェクトの便利な性質の 1 つは、`+` 演算子を使用して、複数のオブジェクトを 1 つのデリゲート インスタンスに割り当てられることです。 マルチキャスト デリゲートには、割り当てられたデリゲートの一覧が含まれています。 マルチキャスト デリゲートを呼び出すと、一覧内のデリゲートが順に呼び出されます。 結合できるのは、同じ型のデリゲートのみです。  
  
 `-` 演算子を使用して、マルチキャスト デリゲートからコンポーネント デリゲートを削除することができます。  
  
## <a name="example"></a>例  
 [!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.MulticastDelegate>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)

