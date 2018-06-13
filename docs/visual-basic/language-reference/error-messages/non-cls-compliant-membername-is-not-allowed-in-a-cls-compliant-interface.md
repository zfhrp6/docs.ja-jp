---
title: 非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: ee533df5e06352034b24651b9173a88d090da0a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594147"
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません
プロパティ、プロシージャ、またはインターフェイスでイベントとしてマークされている`<CLSCompliant(True)>`インターフェイス自体としてマークされている場合`<CLSCompliant(False)>`またはマークされていません。  
  
 インターフェイスに準拠する、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS) に、そのすべてのメンバーは、準拠である必要があります。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40033  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠が必要 インターフェイスのソース コードを制御して、マークとしてインターフェイス`<CLSCompliant(True)>`すべてのメンバーに対応している場合。  
  
-   CLS 準拠する必要があり、インターフェイスのソース コードに制御がない場合、または準拠しているが満たしていない場合は、このメンバーを別のインターフェイスを定義します。  
  
-   このメンバーが、現在インターフェイス内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>をその定義からとしてマークまたは`<CLSCompliant(False)>`です。  
  
## <a name="see-also"></a>関連項目  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
