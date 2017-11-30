---
title: "入れ子になった関数にデリゲート & #39; と互換性のあるシグネチャがありません。&lt;delegatename&gt;& #39 です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>入れ子になった関数にデリゲート & #39; と互換性のあるシグネチャがありません。&lt;delegatename&gt;& #39 です。
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
