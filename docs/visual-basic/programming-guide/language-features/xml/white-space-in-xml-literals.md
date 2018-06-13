---
title: XML リテラルでの空白文字 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649751"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML リテラルでの空白文字 (Visual Basic)
作成時に、Visual Basic コンパイラは、XML リテラルの有意の空白文字だけが組み込まれて、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 意味のない空白文字は組み込まれません。  
  
## <a name="significant-and-insignificant-white-space"></a>有意の空白文字  
 3 つだけの領域で XML リテラルの空白文字が重要です。  
  
-   属性値に含まれる場合。  
  
-   要素のテキスト コンテンツの一部であるし、テキストには、その他の文字も含まれています。  
  
-   要素のテキスト コンテンツの埋め込み式に含まれる場合。  
  
 それ以外の場合、コンパイラとして意味のない空白文字を処理し、で、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]リテラルのオブジェクト。  
  
 XML リテラルに意味のない空白を含める、文字列リテラルの空白文字を含む埋め込み式を使用します。  
  
> [!NOTE]
>  場合、 `xml:space` XML 要素リテラルの属性が表示されます、Visual Basic コンパイラにはで属性が含まれています、<xref:System.Xml.Linq.XElement>オブジェクトが、この属性は、コンパイラが空白文字を処理する方法を変更していないを追加します。  
  
## <a name="examples"></a>使用例  
 次の例には、外部および内部の 2 つの XML 要素が含まれています。 両方の要素には、テキスト コンテンツ内の空白が含まれます。 空白文字と XML 要素のみが含まれているため、外側の要素内の空白は意味はありません。 空白とテキストが含まれているためには、内部の要素内の空白を使用することは重要です。  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 実行すると、このコードは、次のテキストを表示します。  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
