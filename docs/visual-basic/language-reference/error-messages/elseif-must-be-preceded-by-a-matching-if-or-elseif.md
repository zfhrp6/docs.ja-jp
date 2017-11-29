---
title: "&#39; #ElseIf &#39;一致する &#39; #If &#39; の前が必要または &#39; #ElseIf &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords: BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b3a4e809e1108fcd6e116538a1947057e9548ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39; #ElseIf &#39;一致する &#39; #If &#39; の前が必要または &#39; #ElseIf &#39;
`#ElseIf`条件付きコンパイル ディレクティブです。 `#ElseIf`句の前に、対応する必要があります`#If`または`#ElseIf`句。  
  
 **エラー ID:** BC30014  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  確認先行`#If`または`#ElseIf`これから分割されたいない`#ElseIf`によって、中間の条件付きコンパイル ブロックや、間違って配置された`#End If`です。  
  
2.  場合、`#ElseIf`は後に、`#Else`ディレクティブを削除するか、`#Else`に変更して、または、`#ElseIf`です。  
  
3.  他のすべての順序が正しい場合、 `#If` ディレクティブを条件付きコンパイル ブロックの先頭に追加します。  
  
## <a name="see-also"></a>関連項目  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
