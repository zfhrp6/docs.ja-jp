---
title: "Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40025"
  - "vbc40025"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40025"
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このメンバーに指定されたデータ型が、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) のデータ型ではありません。  これは、作成中のコンポーネント自体のエラーではありません。このデータ型は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] および [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ではサポートされています。  ただし、CLS に厳密に準拠するコードで書かれた別のコンポーネントでは、このデータ型がサポートされない可能性があります。  そのようなコンポーネントは、作成中のコンポーネントと正常にやり取りできない場合があります。  
  
 次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC40025  
  
### このエラーを解決するには  
  
-   このコンポーネントが他の [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] コンポーネントとしかやり取りをしない場合、または他のコンポーネントとのやり取りがない場合は、コードを変更する必要はありません。  
  
-   [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 用に作成されていないコンポーネントとやり取りする場合は、リフレクションを使用するかドキュメントを参照すると、そのコンポーネントでこのデータ型がサポートされているかどうかを確認できる可能性があります。  サポートされている場合は、コードを変更する必要はありません。  
  
-   このデータ型をサポートしないコンポーネントとやり取りする場合は、最も近い CLS 準拠型にデータ型を置き換える必要があります。  たとえば、2,147,483,647 を超える値の範囲が必要でない場合は、`UInteger` の代わりに `Integer` を使用できます。  範囲を拡張する必要がある場合は、`UInteger` を `Long` に置き換えることができます。  
  
-   オートメーションまたは COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] とは異なることに注意してください。  たとえば `uint` は、他の環境では多くの場合 16 ビットです。  そのようなコンポーネントに 16 ビットの引数を渡す場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のマネージ コードで、`UInteger` 型ではなく `UShort` 型として宣言してください。  
  
## 参照  
 [リフレクション](../Topic/Reflection%20in%20the%20.NET%20Framework.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)