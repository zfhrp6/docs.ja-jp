---
title: "名前&lt;membername&gt; CLS 準拠ではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 6a678c66580a7917a3869aac81418152130debff
ms.lasthandoff: 03/13/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>名前&lt;membername&gt; CLS 準拠ではありません
アセンブリとしてマークされている`<CLSCompliant(True)>`晒すことにアンダー スコアで始まる名前を持つメンバー (`_`)。  
  
 プログラミング要素に準拠しているが、1 つまたは複数アンダー スコアを含めることができます、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) に始めることはできません、アンダー スコアでします。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
 適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40031  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ソース コードに制御がある場合は、メンバーの名前を変更して、アンダー スコアで始まらないようにします。  
  
-   メンバーの名前は変更しないことが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義から、またはマークとしてして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。 アセンブリをマークすることも`<CLSCompliant(True)>`です。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素名](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
