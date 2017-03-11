---
title: "省略可能なパラメーター &lt;パラメーター名&gt; に対する省略可能な値の型が CLS に準拠していません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "BC40042"
  - "vbc40042"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40042"
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# 省略可能なパラメーター &lt;パラメーター名&gt; に対する省略可能な値の型が CLS に準拠していません
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャは `<CLSCompliant(True)>` に設定されていますが、非準拠の型が既定値である [Optional](../../../visual-basic/language-reference/modifiers/optional.md) パラメーターが宣言されています。  
  
 プロシージャを[言語への非依存性および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。 これは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に適用されます。 また、省略可能なパラメーターの既定値にも適用されます。  
  
 次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> 属性を適用するときは、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40042  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   省略可能なパラメーターにこの特定の型の既定値を設定する必要がある場合は、<xref:System.CLSCompliantAttribute> を削除します。 プロシージャは CLS 準拠になりません。  
  
-   プロシージャを CLS 準拠にする必要がある場合は、この既定値の型を、最も近い CLS 準拠型に変更します。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
-   オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] とは異なることに注意してください。 たとえば、他の多くの環境では `int` は 16 ビットです。 このようなコンポーネントから 16 ビット整数を受け取る場合、マネージ [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コードでは、`Integer` ではなく `Short` を宣言してください。  
  
## <a name="see-also"></a>関連項目  
 [\<PAVE OVER> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)