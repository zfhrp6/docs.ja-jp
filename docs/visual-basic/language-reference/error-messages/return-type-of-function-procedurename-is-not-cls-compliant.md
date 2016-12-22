---
title: "Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40027"
  - "vbc40027"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40027"
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Function` プロシージャが `<CLSCompliant(True)>` でマーク付けされていますが、戻り値の型が `<CLSCompliant(False)>` でマーク付けされているか、マークが付けられていないか、または非準拠の型であるため不適切です。  
  
 プロシージャを[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 準拠にするためには、CLS 準拠の型のみを使用する必要があります。  このことは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に当てはまります。  
  
 次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] データ型は CLS に準拠していません。  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <xref:System.CLSCompliantAttribute> をプログラミング要素に適用するときは、属性の `isCompliant` パラメーターを `True` または `False` に設定して準拠または非準拠を示します。  このパラメーターの既定値はありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC40027  
  
### このエラーを解決するには  
  
-   `Function` プロシージャがこの特定の型を返す必要がある場合は、<xref:System.CLSCompliantAttribute> を削除します。  このプロシージャは CLS 準拠になりません。  
  
-   `Function` プロシージャを CLS に準拠させる必要がある場合は、戻り値の型を CLS に準拠した最も近い型に変更します。  たとえば、2,147,483,647 を超える値の範囲が必要でない場合は、`UInteger` の代わりに `Integer` を使用できます。  範囲を拡張する必要がある場合は、`UInteger` を `Long` に置き換えることができます。  
  
-   オートメーションまたは COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] とは異なることに注意してください。  たとえば `int` は、他の環境では多くの場合 16 ビットです。  そのようなコンポーネントに 16 ビットの整数を返す場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のマネージ コードで、`Integer` 型ではなく `Short` 型で宣言してください。  
  
## 参照  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)