---
title: '方法 : XML 子孫要素にアクセスする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 6d41844b540631df96740ce56818c125cf85e928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648487"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>方法 : XML 子孫要素にアクセスする (Visual Basic)
この例では、descendant 軸のプロパティを使用して、指定した名前を持ち、XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。 具体的を使用して、`Value`プロパティをコレクション内の最初の要素の値を取得、 `name` descendant 軸のプロパティを返します。 `name`子孫軸プロパティというすべての要素を取得する`name`に含まれる、`contacts`オブジェクト。 またこの例では、`phone`という名前のすべての子孫にアクセスする子孫軸プロパティ`phone`に含まれる、`contacts`オブジェクト。  
  
## <a name="example"></a>例  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System.Xml.Linq> 名前空間への参照  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [XML 子孫軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
