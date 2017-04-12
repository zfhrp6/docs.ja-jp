---
title: "XML 属性軸プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
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
ms.openlocfilehash: 94211f7c951976426ba17e73df214444a6c227b4
ms.lasthandoff: 03/13/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 属性軸プロパティ (Visual Basic)
属性の値にアクセスできるように、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素に、または<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。  
  
## <a name="syntax"></a>構文  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>指定項目  
 `object`  
 必須です。 <xref:System.Xml.Linq.XElement>オブジェクトまたは一連の<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。  
  
 .@  
 必ず指定します。 属性軸プロパティの開始を示します。  
  
 <  
 省略可能です。 属性の名前の先頭を示しますと`attribute`で有効な識別子ではない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
 `attribute`  
 必須です。 フォームにアクセスする属性の名前 [`prefix`:]`name`します。  
  
|パーツ|説明|  
|----------|-----------------|  
|`prefix`|省略可能です。 属性の XML 名前空間プレフィックス。 `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。|  
|`name`|必須です。 属性のローカル名。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。|  
  
 \>  
 省略可能です。 属性の名前の末尾を示すときに`attribute`で有効な識別子ではありません[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
## <a name="return-value"></a>戻り値  
 値を含む文字列`attribute`します。 属性名が存在しない場合`Nothing`が返されます。  
  
## <a name="remarks"></a>コメント  
 XML 属性軸プロパティを使用するには名を使用して属性の値にアクセスする、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素から、または<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。 名前で属性値を取得またはスコアで始まる新しい名前を指定することによって要素に新しい属性を追加することができます、@ 識別子。  
  
 使用する XML 属性を参照するとき、@ 識別子、属性の値が文字列として返され、明示的に指定する必要はありません、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティ</xref:System.Xml.Linq.XAttribute.Value%2A>。  
  
 XML 属性の名前付け規則と名前付け規則について異なる[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]識別子。 Visual Basic の有効な識別子ではない名前を持つ XML 属性にアクセスするには、山かっこで名前を囲む (\<と >)。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 属性軸プロパティの名前は、XML 名前空間プレフィックスだけを使用して、グローバルに宣言を使用できます、`Imports`ステートメントです。 XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
## <a name="example"></a>例  
 次の例は、XML 属性の名前付きの値を取得する方法を示しています。`type`という XML 要素のコレクションから`phone`します。  
  
 [!code-vb[VbXMLSamples&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>例  
 次の例では、両方の XML 要素の属性の宣言の一部として、XML では、動的に、属性のインスタンスを追加して作成する方法、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。 `type`属性が宣言によって作成されると、 `owne`r 属性を動的に作成します。  
  
 [!code-vb[VbXMLSamples #&44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>例  
 次の例では、山かっこでは構文を使用してという名前の XML 属性の値を取得`number-type`で有効な識別子ではない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
 [!code-vb[VbXMLSamples&#13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone type: work`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 使用して、名前空間のプレフィックスを XML リテラルを作成し、修飾名を持つ最初の子ノードへのアクセス"`ns:name`"です。  
  
 [!code-vb[VbXMLSamples&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone type: home`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>   
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
