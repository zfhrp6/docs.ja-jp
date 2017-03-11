---
title: "Type &lt;typename&gt; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40041"
  - "vbc40041"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40041"
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Type &lt;typename&gt; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数、プロパティ、または関数の戻り値が、CLS 準拠ではないデータ型で宣言されています。  
  
 アプリケーションを [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠させるためには、CLS 準拠の型のみを使う必要があります。  
  
 次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **Error ID:** BC40041  
  
### このエラーを解決するには  
  
-   アプリケーションを CLS に準拠させる必要がある場合は、この要素のデータ型を CLS に準拠した最も近い型に変更します。  たとえば、2,147,483,647 を超える値の範囲が必要でない場合は、`UInteger` の代わりに `Integer` を使用できます。  範囲を拡張する必要がある場合は、`UInteger` を `Long` に置き換えることができます。  
  
-   アプリケーションを CLS に準拠させる必要がない場合は、何も変更する必要はありません。  ただし、準拠しないことは頭に入れておいてください。  
  
## 参照  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)