---
title: イベント&#39; &lt;eventname1&gt; &#39;イベントを実装できません&#39; &lt;eventname2&gt; &#39;インターフェイスで&#39;&lt;インターフェイス&gt;&#39;ため。デリゲート型&#39; &lt;delegate1&gt; &#39;と&#39; &lt;delegate2&gt; &#39;が一致しません
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 5c62b2f3e94de1c2a8919ec30b1ef106186bee11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589157"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>イベント&#39; &lt;eventname1&gt; &#39;イベントを実装できません&#39; &lt;eventname2&gt; &#39;インターフェイスで&#39;&lt;インターフェイス&gt;&#39;ため。デリゲート型&#39; &lt;delegate1&gt; &#39;と&#39; &lt;delegate2&gt; &#39;が一致しません
イベントのデリゲート型がインターフェイスでイベントのデリゲート型と一致しないために、Visual Basic では、イベントを実装できません。 このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。 実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。  
  
 **エラー ID:** BC31423  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   イベントを個別に実装します。  
  
     または  
  
-   インターフェイスを使用して、イベントを定義、`As`構文と同じデリゲート型を指定します。  
  
## <a name="see-also"></a>関連項目  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
