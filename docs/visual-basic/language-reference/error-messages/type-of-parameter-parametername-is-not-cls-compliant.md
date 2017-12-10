---
title: "パラメーター &#39; の種類&lt;parametername&gt;&#39; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords: BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5fc981f5de5c4baa9a47e04af16966ea06fa10ad
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>パラメーター &#39; の種類&lt;parametername&gt;&#39; CLS 準拠ではありません
プロシージャとしてマークされている`<CLSCompliant(True)>`としてマークされている型とパラメーターを宣言していますが、 `<CLSCompliant(False)>`、マークされていないか修飾されていません、非準拠の型になっているためです。  
  
 プロシージャを[言語への非依存性および言語非依存コンポーネント](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。 これは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に適用されます。  
  
 次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40028  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャは、この特定の型のパラメーターを受け取る必要があります、削除、<xref:System.CLSCompliantAttribute>です。 プロシージャは CLS 準拠になりません。  
  
-   プロシージャは、CLS に準拠する必要があります、最も近い CLS 準拠型にこのパラメーターの型を変更します。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
-   オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] とは異なることに注意してください。 たとえば、他の多くの環境では `int` は 16 ビットです。 このようなコンポーネントから 16 ビット整数を受け取る場合、マネージ [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コードでは、`Integer` ではなく `Short` を宣言してください。  
  
## <a name="see-also"></a>関連項目  
 [\<経由で PAVE > CLS 準拠コードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
