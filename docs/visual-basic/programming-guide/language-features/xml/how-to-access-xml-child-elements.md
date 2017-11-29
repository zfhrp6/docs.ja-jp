---
title: "方法 : XML 子要素にアクセスする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d3a708b787ad38f08d4673d4003db839f6cf6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>方法 : XML 子要素にアクセスする (Visual Basic)
この例では、軸のプロパティを XML 要素で指定した名前を持つすべての XML 子要素にアクセスする子を使用する方法を示します。 具体的を使用して、<xref:System.Xml.Linq.XElement.Value%2A>プロパティをコレクション内の最初の要素の値を取得、`name`子軸プロパティを返します。 `name`子軸プロパティを取得という名前の子要素がすべて`phone`で、`contact`オブジェクト。 またこの例では、`phone`というすべての子要素にアクセスする子軸プロパティ`phone`に含まれる、`contact`オブジェクト。  
  
## <a name="example"></a>例  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System.Xml.Linq> 名前空間への参照  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
