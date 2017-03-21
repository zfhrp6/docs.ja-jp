---
title: "XML リテラル (Visual Basic) での空白文字 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
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
ms.openlocfilehash: b98a88696f24cc0b95401812471d13acea4faa6d
ms.lasthandoff: 03/13/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML リテラルでの空白文字 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の作成時にコンパイラに XML リテラルの有意の空白文字だけが組み込まれて、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。 余分な空白文字は組み込まれません。  
  
## <a name="significant-and-insignificant-white-space"></a>有意の空白文字  
 XML リテラルの空白文字、重要な&3; つのみ分類されます。  
  
-   属性値に含まれる場合。  
  
-   要素のテキスト コンテンツの一部であるし、テキストには、その他の文字も含まれています。  
  
-   要素のテキスト コンテンツに組み込み式に含まれる場合。  
  
 それ以外の場合、コンパイラとして意味のない空白文字を処理しでは、含まれません、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]リテラルのオブジェクト。  
  
 余分な空白を XML リテラルに含めるには、空白文字をリテラル文字列を含む埋め込み式を使用します。  
  
> [!NOTE]
>  場合、`xml:space`リテラルで XML 要素に属性が表示されます、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラには、属性が用意されています、<xref:System.Xml.Linq.XElement>オブジェクトはこの属性は、コンパイラが空白文字を処理する方法を変更していない追加しようとします</xref:System.Xml.Linq.XElement>。  
  
## <a name="examples"></a>例  
 次の例には、外側と内側の&2; つの XML 要素が含まれています。 両方の要素には、そのテキストの内容に空白が含まれています。 空白と XML 要素のみが含まれているため、外側の要素内の空白は意味はありません。 空白文字とテキストが含まれているために、内部の要素内の空白は重要です。  
  
 [!code-vb[VbXMLSamples #&29;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 実行すると、このコードは、次のテキストを表示します。  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
