---
title: "&quot;&lt;elementname&gt;&quot; は古い (Visual Basic 警告) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ccec3b2659502c84dd4db9c9c4d796362958030b
ms.lasthandoff: 03/13/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>'&lt;elementname&gt;' は古い (Visual Basic 警告)
ステートメントでマークされているプログラミング要素にアクセスしようとしました、<xref:System.ObsoleteAttribute>属性と、警告として扱うディレクティブ。</xref:System.ObsoleteAttribute> 。  
  
 使用中と不要になった<xref:System.ObsoleteAttribute>を</xref:System.ObsoleteAttribute>適用することで任意のプログラミング要素をマークすることができます。 これを行う場合は、属性を設定することができます<xref:System.ObsoleteAttribute.IsError%2A>プロパティを`True`または`False`</xref:System.ObsoleteAttribute.IsError%2A>。 `True`に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。 `False`に設定するか、または既定の `False`にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。  
  
 既定では、このメッセージは警告であるため、<xref:System.ObsoleteAttribute.IsError%2A>の<xref:System.ObsoleteAttribute>は`False`</xref:System.ObsoleteAttribute></xref:System.ObsoleteAttribute.IsError%2A>。 警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
 **エラー ID:** BC40008  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ソース コード参照の要素名のスペルが正しいことを確認します。  
  
## <a name="see-also"></a>関連項目  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)

