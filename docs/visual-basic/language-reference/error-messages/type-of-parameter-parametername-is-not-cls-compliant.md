---
title: "Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40028"
  - "bc40028"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40028"
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャが `<CLSCompliant(True)>` としてマークされていますが、宣言しているパラメーターの型が `<CLSCompliant(False)>` としてマークされているか、マークされていないか、非準拠の型であるため不適切です。  
  
 プロシージャを[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 準拠にするためには、CLS 準拠の型のみを使用する必要があります。  このことは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に当てはまります。  
  
 次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <xref:System.CLSCompliantAttribute> をプログラミング要素に適用するときは、属性の `isCompliant` パラメーターを `True` または `False` に設定して準拠または非準拠を示します。  このパラメーターの既定値はありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC40028  
  
### このエラーを解決するには  
  
-   プロシージャがこの特定の型のパラメーターを取る必要がある場合は、<xref:System.CLSCompliantAttribute> を削除します。  このプロシージャは CLS 準拠になりません。  
  
-   プロシージャを CLS 準拠にする必要がある場合は、このパラメーターの型を、最も近い CLS 準拠型に変更します。  たとえば、2,147,483,647 を超える値の範囲が必要でない場合は、`UInteger` の代わりに `Integer` を使用できます。  範囲を拡張する必要がある場合は、`UInteger` を `Long` に置き換えることができます。  
  
-   オートメーションまたは COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] とは異なることに注意してください。  たとえば `int` は、他の環境では多くの場合 16 ビットです。  そのようなコンポーネントから 16 ビットの整数を受け取る場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のマネージ コードで、`Integer` 型ではなく `Short` 型として宣言してください。  
  
## 参照  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)