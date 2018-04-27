---
title: Visual Basic での XML へのアクセス
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 064e4b224d37172b8f79e57c73164b90186ef922
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-xml-in-visual-basic"></a>Visual Basic での XML へのアクセス
Visual Basic XML 軸のプロパティにアクセスして移動するために用意[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]構造体。 これらのプロパティは、XML の名前を指定する要素と属性にアクセスするために、特別な構文を使用します。  
  
 次の表は、XML 要素と Visual Basic における属性にアクセスできるようにする言語機能を一覧表示します。  
  
### <a name="xml-axis-properties"></a>XML 軸プロパティ  
  
|プロパティの説明|例|説明|  
|--------------------------|-------------|-----------------|  
|*child 軸*|`contact.<phone>`|すべてを取得`phone`要素の子要素である、`contact`要素。|  
|*attribute 軸*|`phone.@type`|すべてを取得`type`の属性、`phone`要素。|  
|*descendant 軸*|`contacts...<name>`|すべてを取得`name`の要素、`contacts`に関係なく発生する階層の深さの要素。|  
|*拡張機能インデクサー*|`contacts...<name>(0)`|最初に取得`name`シーケンスから要素。|  
|*値*|`contacts...<name>.Value`|シーケンスの最初のオブジェクトの文字列形式を取得または`Nothing`シーケンスが空の場合。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: XML 子孫要素にアクセスする](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 子孫軸プロパティを使用して、指定した名前を持ち、指定された XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。  
  
 [方法: XML 子要素にアクセスする](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 軸のプロパティを XML 要素で指定した名前を持つすべての XML 子要素にアクセスする子を使用する方法を示します。  
  
 [方法: XML 属性にアクセスする](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 属性軸プロパティを使用して XML 要素で指定した名前を持つすべての XML 属性にアクセスする方法を示します。  
  
 [方法 : XML 名前空間プレフィックスを宣言して使用する](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 XML 名前空間プレフィックスを宣言し、それを使用して作成し、XML 要素にアクセスする方法を示します。  
  
## <a name="related-sections"></a>関連項目  
 [XML 軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 さまざまな XML アクセス プロパティを説明するセクションへのリンクを提供します。  
  
 [Visual Basic における LINQ to XML の概要](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 使用する方法について紹介[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic でします。  
  
 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Visual Basic での XML リテラルの使用の概要を提供します。  
  
 [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 読み込みと Visual Basic における XML を変更するセクションへのリンクを提供します。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 使用する方法を説明するセクションへのリンクを提供[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic でします。
