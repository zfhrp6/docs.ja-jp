---
title: "GetXmlNamespace 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
dev_langs:
- VB
helpviewer_keywords:
- GetXmlNamespace operator
- GetXmlNamespace keyword
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
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
ms.openlocfilehash: 929ba4edae9e155245228670424a3898896da807
ms.lasthandoff: 03/13/2017

---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 演算子 (Visual Basic)
取得、<xref:System.Xml.Linq.XNamespace>指定された XML 名前空間プレフィックスに対応するオブジェクト</xref:System.Xml.Linq.XNamespace>。  
  
## <a name="syntax"></a>構文  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 省略可能です。 XML 名前空間プレフィックスを識別する文字列。 指定した場合、この文字列は有効な XML 識別子である必要があります。 詳細については、次を参照してください。[宣言されている XML 要素の名前と属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。 プレフィックスが指定されていない場合は、既定の名前空間が返されます。 既定の名前空間が指定されていない場合は、空の名前空間が返されます。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XNamespace>XML 名前空間プレフィックスに対応するオブジェクト</xref:System.Xml.Linq.XNamespace>。  
  
## <a name="remarks"></a>コメント  
 `GetXmlNamespace`演算子を取得、 <xref:System.Xml.Linq.XNamespace>XML 名前空間プレフィックスに対応するオブジェクト`xmlNamespacePrefix`</xref:System.Xml.Linq.XNamespace>。  
  
 XML リテラルと XML 軸プロパティに直接 XML 名前空間プレフィックスを使用することができます。 ただし、使用する必要があります、`GetXmlNamespace`名前空間プレフィックスに変換する演算子、<xref:System.Xml.Linq.XNamespace>オブジェクトの前に、コードで使用することができます</xref:System.Xml.Linq.XNamespace>。 非修飾要素名を追加する、<xref:System.Xml.Linq.XNamespace>完全修飾を取得するオブジェクト<xref:System.Xml.Linq.XName>オブジェクトを指定[!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]メソッドが必要です</xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XNamespace>。  
  
## <a name="example"></a>例  
 次の例ではインポート`ns`XML 名前空間プレフィックスとして。 使用して、名前空間のプレフィックスを XML リテラルを作成し、修飾名を持つ最初の子ノードにアクセス`ns:phone`します。 これは、後、その子ノードを渡します、`ShowName`を使用して、修飾名を構築するサブルーチン、`GetXmlNamespace`演算子。 `ShowName`サブルーチンは、修飾名を渡します、<xref:System.Xml.Linq.XNode.Ancestors%2A>親を取得するメソッド`ns:contact`ノード</xref:System.Xml.Linq.XNode.Ancestors%2A>。  
  
 [!code-vb[VbXMLSamples #&38;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 呼び出すと`TestGetXmlNamespace.RunSample()`、次のテキストを含むメッセージ ボックスが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Visual Basic における XML へのアクセス](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
