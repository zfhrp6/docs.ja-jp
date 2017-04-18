---
title: "非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
dev_langs:
- VB
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
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
ms.openlocfilehash: 2861ef22c9307e5bd7d2eabf4f6e37bbd9086345
ms.lasthandoff: 03/13/2017

---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません
プロパティ、プロシージャ、またはインターフェイスのイベントとしてマークされている`<CLSCompliant(True)>`インターフェイス自体としてマークされている場合`<CLSCompliant(False)>`またはマークされていません。  
  
 インターフェイスに対応して、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、すべてのメンバーは、対応である必要があります。  
  
 適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40033  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠をする必要があり、インターフェイスのソース コードに制御をマークされているインターフェイス`<CLSCompliant(True)>`すべてのメンバーに対応している場合。  
  
-   CLS 準拠を必要となり、インターフェイスのソース コードを管理していない場合、または準拠しているが明確でない場合は、このメンバーを別のインターフェイスを定義します。  
  
-   このメンバーが、現在のインターフェイス内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義からまたはとしてマークして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。  
  
## <a name="see-also"></a>関連項目  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
