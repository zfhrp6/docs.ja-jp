---
title: エラーが発生していないときに Resume を実行することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597876"
---
# <a name="resume-without-error"></a>エラーが発生していないときに Resume を実行することはできません。
A`Resume`ステートメントは、外部のエラー処理コードを表示またはコードは、エラーがなかった場合でも、エラー ハンドラーにジャンプします。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  移動、`Resume`ステートメント、エラー ハンドラーを削除したりします。  
  
2.  ラベルにジャンプは、プロシージャ間発生することはできないため、エラー ハンドラーを識別するラベルをプロシージャ内で検索します。 対象として指定されている重複するラベルを検索する場合、`GoTo`ステートメントではなく、`On Error GoTo`ステートメントでは、目的の宛先と一致する行のラベルを変更します。  
  
## <a name="see-also"></a>関連項目  
 [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
