---
title: "構造体 &#39;&lt;structurename&gt;&#39; には、少なくとも 1 つのインスタンス メンバー変数、またはマークされていないには、少なくとも 1 つのインスタンスのイベント宣言 &#39; に含める必要がありますカスタム &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords: BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>構造体 &#39;&lt;structurename&gt;&#39; には、少なくとも 1 つのインスタンス メンバー変数、またはマークされていないには、少なくとも 1 つのインスタンスのイベント宣言 &#39; に含める必要がありますカスタム &#39;
構造体の定義は、すべての非共有変数または非共有のカスタム イベントには含まれません。  
  
 すべての構造体を変数または総称してすべてのインスタンスに (共有) の代わりに特定のインスタンスに適用されるイベントのいずれかが適用される場合があります ([Shared](../../../visual-basic/language-reference/modifiers/shared.md))。 非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。 さらに、非共有変数がなく、1 つだけの非共有イベントがある場合は、そのイベントすることはできません、`Custom`イベント。  
  
 **エラー ID:** BC30941  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   少なくとも 1 つの変数またはイベントではない定義`Shared`です。 1 つだけイベントを定義する場合は、非カスタムと非共有があります。  
  
## <a name="see-also"></a>関連項目  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [方法 : 構造体を宣言する](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
