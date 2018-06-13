---
title: 入れ子になった関数にデリゲートと互換性のあるシグネチャがない&#39; &lt;delegatename&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594472"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>入れ子になった関数にデリゲートと互換性のあるシグネチャがない&#39; &lt;delegatename&gt;&#39;
ラムダ式は、互換性のないシグネチャを持つデリゲートに割り当てられています。 たとえば、次のコードでは、委任`Del`2 つの整数パラメーターします。  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 1 つの引数があるラムダ式は型として宣言されている場合、エラーが発生`Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **エラー ID:** BC36532  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   シグネチャに互換性があるようには、デリゲートの定義または割り当てられているラムダ式のいずれかを調整します。  
  
## <a name="see-also"></a>関連項目  
 [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
