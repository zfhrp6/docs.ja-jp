---
title: "GetXmlNamespace 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 演算子 (Visual Basic)
取得、<xref:System.Xml.Linq.XNamespace>指定された XML 名前空間プレフィックスに対応するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 省略可能です。 XML 名前空間プレフィックスを識別する文字列。 指定した場合、この文字列は有効な XML 識別子にする必要があります。 詳細については、次を参照してください。[宣言されている XML 要素の名前および属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。 プレフィックスが指定されていない場合は、既定の名前空間が返されます。 既定の名前空間が指定されていない場合は、空の名前空間が返されます。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XNamespace> XML 名前空間プレフィックスに対応するオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `GetXmlNamespace`演算子を取得、<xref:System.Xml.Linq.XNamespace>オブジェクト XML 名前空間プレフィックスに対応する`xmlNamespacePrefix`です。  
  
 XML リテラルおよび XML 軸のプロパティで直接 XML 名前空間プレフィックスを使用することができます。 ただし、使用する必要があります、`GetXmlNamespace`に名前空間プレフィックスを変換する演算子、<xref:System.Xml.Linq.XNamespace>オブジェクトの前に、コードで使用することができます。 修飾されていない要素名を追加することができます、<xref:System.Xml.Linq.XNamespace>完全修飾を取得するオブジェクト<xref:System.Xml.Linq.XName>オブジェクト、どの多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]メソッドを必要とします。  
  
## <a name="example"></a>例  
 次の例ではインポート`ns`XML 名前空間プレフィックスとして。 XML リテラルを作成し、修飾名を持つ最初の子ノードにアクセスする、名前空間のプレフィックスを使用して`ns:phone`です。 これは、後、その子ノードを渡します、`ShowName`を使用して、修飾名を構築するサブルーチン、`GetXmlNamespace`演算子。 `ShowName`修飾名を渡しますサブルーチン、<xref:System.Xml.Linq.XNode.Ancestors%2A>親を取得するメソッド`ns:contact`ノード。  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 呼び出すと`TestGetXmlNamespace.RunSample()`、次のテキストを含むメッセージ ボックスが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Visual Basic での XML へのアクセス](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
