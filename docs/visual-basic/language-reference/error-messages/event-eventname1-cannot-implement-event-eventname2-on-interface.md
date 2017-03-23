---
title: "イベント &quot;&lt;eventname1&gt;&quot;イベントを実装できない&quot;&lt;eventname2&gt;&quot;にインターフェイス&quot;&lt;インターフェイス&gt;&quot; ため、デリゲート型の&lt;delegate1&gt;&quot;と&quot;&lt;delegate2&gt;&quot; が一致しない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
dev_langs:
- VB
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b6253b3e9ad07c3715c55a8cfd0891792b45a452
ms.lasthandoff: 03/13/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>イベント '&lt;eventname1&gt;'イベントを実装できない'&lt;eventname2&gt;'にインターフェイス'&lt;インターフェイス&gt;' ため、デリゲート型の&lt;delegate1&gt;'と'&lt;delegate2&gt;' が一致しません。
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]イベントのデリゲート型がインターフェイスでイベントのデリゲート型と一致しないために、イベントを実装することはできません。 このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。 実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは&2; つ以上のイベントを実装することができます。  
  
 **エラー ID:** BC31423  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   イベントを個別に実装します。  
  
     または  
  
-   インターフェイスを使用して、イベントを定義、`As`構文し、同じデリゲート型を指定します。  
  
## <a name="see-also"></a>関連項目  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
