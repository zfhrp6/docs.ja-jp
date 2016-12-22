---
title: "Names of Declared XML Elements and Attributes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarations [XML in Visual Basic]"
  - "element names [XML in Visual Basic]"
  - "names in XML literals"
  - "attribute names [XML in Visual Basic]"
  - "XML literals [Visual Basic], element names"
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Names of Declared XML Elements and Attributes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

ここでは、XML リテラルでの XML の要素と属性の名前付けに関する [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のガイドラインを示します。XML リテラルでは、ローカル名または修飾名を指定できます。  修飾名は、XML 名前空間プレフィックス、コロン、およびローカル名で構成されます。  XML 名前空間プレフィックスの詳細については、「[XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)」を参照してください。  
  
## 規則  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 内の要素または属性のローカル名は、次の規則に従う必要があります。  
  
-   名前空間で始めることができるが、  アルファベットまたはアンダースコア \(`_`\) で始める必要がある。  
  
-   アルファベット、10 進数、アンダースコア、ピリオド \(.\)、ハイフン \(\-\) 以外の文字は含まない。  
  
-   長さが 1,024 文字を超えない。  
  
-   名前に含まれるコロンは名前空間の区切りを示すため、  特定の名前に対する XML 名前空間を指定する以外にはコロンは使用できない。  
  
 さらに、次のガイドラインに従う必要があります。  
  
-   XML 1.0 仕様では、大文字と小文字のあらゆる組み合わせによる文字列 "xml" で始まるすべての名前が予約されているため、  要素および属性の名前には、このような名前は使用できない。  
  
### 名前の長さのガイドライン  
 実際の問題として、名前は、要素の特性を明確に区別しながら可能な限り短いものである必要があります。  これによってコードが読みやすくなり、行の長さとソース ファイルのサイズを小さくできます。  
  
 一方で、名前は、要素およびコードでの要素の使用方法を適切に記述できる長さである必要があります。  これは、コードの読みやすさの点で重要です。  作成者以外のだれかがコードを理解しようとした場合や、作成者自身が作成後しばらくたってからコードを見た場合に、適切な要素名が付いていると時間を節約できます。  
  
## 名前の大文字と小文字の区別  
 XML 要素名では、大文字と小文字が区別されます。  したがって、大文字と小文字のみが異なる 2 つの名前を、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは異なる名前として解釈します。  たとえば、`ABC` と `abc` は、異なる要素を参照するものとして解釈されます。  
  
## XML 名前空間  
 XML 要素リテラルを作成するときは、要素名に XML 名前空間プレフィックスを指定できます。  詳細については、「[XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)」を参照してください。  
  
## 参照  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)