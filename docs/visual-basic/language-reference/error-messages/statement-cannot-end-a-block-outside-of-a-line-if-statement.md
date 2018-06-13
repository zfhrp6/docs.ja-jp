---
title: ステートメントは、行の外側でブロックを終了できません&#39;場合&#39;ステートメント
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596685"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>ステートメントは、行の外側でブロックを終了できません&#39;場合&#39;ステートメント
単一行`If`ステートメントがコロン (:) のうちの 1 つで区切られた複数のステートメントを含む、`End`単一行の外部のコントロール ブロックのステートメント`If`です。 単一行`If`ステートメントは使用しないで、`End If`ステートメントです。  
  
 **エラー ID:** BC32005  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   単一行を移動`If`ステートメントを含むコントロール ブロックの外側、`End If`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
