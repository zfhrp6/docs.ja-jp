---
title: 名前&lt;membername&gt; CLS 準拠ではありません
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 26ff13de461d5a96724868b7928129a326cdf1d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593343"
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>名前&lt;membername&gt; CLS 準拠ではありません
アセンブリとしてマークされている`<CLSCompliant(True)>`アンダー スコアで始まる名前を持つメンバーを公開するが、(`_`)。  
  
 プログラミング要素に準拠するためには、1 つまたは複数アンダー スコアを含めることができます、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS) に始めることはできません、アンダー スコアを使用します。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40031  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ソース コードを使用していればは、メンバー名を変更してから、アンダー スコアで始まらないようにします。  
  
-   メンバーの名前は変更しないことを必要とする場合は、削除、<xref:System.CLSCompliantAttribute>をその定義からとしてマークまたは`<CLSCompliant(False)>`です。 アセンブリをマークすることも`<CLSCompliant(True)>`します。  
  
## <a name="see-also"></a>関連項目  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  

