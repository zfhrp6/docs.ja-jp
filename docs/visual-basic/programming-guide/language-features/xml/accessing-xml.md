---
title: "Visual Basic における XML にアクセスする |Microsoft ドキュメント"
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
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 215f057f0b4d884369aad53cbbdbb98f240b56c4
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-xml-in-visual-basic"></a>Visual Basic での XML へのアクセス
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML 軸プロパティにアクセスして、移動[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]構造体。 これらのプロパティは、XML の名前を指定する要素と属性にアクセスするために、特別な構文を使用します。  
  
 次の表に、XML 要素と属性にアクセスするための言語機能[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。  
  
### <a name="xml-axis-properties"></a>XML 軸プロパティ  
  
|プロパティの説明|例|説明|  
|--------------------------|-------------|-----------------|  
|*child 軸*|`contact.<phone>`|すべてを取得します`phone`要素の子要素である、`contact`要素。|  
|*attribute 軸*|`phone.@type`|すべてを取得します`type`の属性、`phone`要素。|  
|*子孫軸*|`contacts...<name>`|すべてを取得します`name`の要素、`contacts`に関係なく、発生した階層の深さの要素。|  
|*拡張機能インデクサー*|`contacts...<name>(0)`|最初の取得`name`シーケンスから要素。|  
|*value*|`contacts...<name>.Value`|シーケンスの最初のオブジェクトの文字列形式を取得または`Nothing`シーケンスが空の場合。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: XML 子孫要素にアクセスする](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 子孫軸プロパティを使用して、指定の名前を持ち、指定された XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。  
  
 [方法: XML 子要素にアクセスする](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 軸にアクセスするプロパティを XML 要素で指定した名前を持つすべての XML 子要素の子を使用する方法を示します。  
  
 [方法: XML 属性にアクセスする](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 属性軸プロパティを使用して XML 要素で指定した名前を持つすべての XML 属性にアクセスする方法を示します。  
  
 [方法 : XML 名前空間プレフィックスを宣言して使用する](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 XML 名前空間プレフィックスを宣言し、これを作成し、XML 要素にアクセスに使用する方法を示します。  
  
## <a name="related-sections"></a>関連項目  
 [XML 軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 さまざまな XML アクセス プロパティを説明するセクションへのリンクを提供します。  
  
 [Visual Basic における LINQ to XML の概要](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 使用の概要については、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] Visual Basic でします。  
  
 [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Visual Basic で XML リテラルを使用するための概要を提供します。  
  
 [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 読み込みと Visual Basic における XML の修正についてのセクションへのリンクを提供します。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 使用する方法を説明するセクションへのリンクを提供[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Visual Basic でします。
