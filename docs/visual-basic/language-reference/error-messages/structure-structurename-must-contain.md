---
title: 構造体&#39; &lt;structurename&gt; &#39;に少なくとも 1 つのインスタンス メンバー変数またはマークされていない 1 つ以上のインスタンス イベントの宣言を含める必要があります&#39;カスタム&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594500"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>構造体&#39; &lt;structurename&gt; &#39;に少なくとも 1 つのインスタンス メンバー変数またはマークされていない 1 つ以上のインスタンス イベントの宣言を含める必要があります&#39;カスタム&#39;
構造体の定義は、すべての非共有変数または非共有のカスタム イベントには含まれません。  
  
 すべての構造体を変数または総称してすべてのインスタンスに (共有) の代わりに特定のインスタンスに適用されるイベントのいずれかが適用される場合があります ([Shared](../../../visual-basic/language-reference/modifiers/shared.md))。 非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。 さらに、非共有変数がなく、1 つだけの非共有イベントがある場合は、そのイベントすることはできません、`Custom`イベント。  
  
 **エラー ID:** BC30941  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   少なくとも 1 つの変数またはイベントではない定義`Shared`です。 1 つだけイベントを定義する場合は、非カスタムと非共有があります。  
  
## <a name="see-also"></a>関連項目  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [方法 : 構造体を宣言する](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
