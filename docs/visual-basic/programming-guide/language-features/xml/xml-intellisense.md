---
title: "Visual Basic における XML IntelliSense |Microsoft ドキュメント"
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
- Visual Basic code, XML
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
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
ms.openlocfilehash: 8c43db3d2010e4fa92eebeec8a973c50052b1340
ms.lasthandoff: 03/13/2017

---
# <a name="xml-intellisense-in-visual-basic"></a>Visual Basic における XML IntelliSense
Visual Basic コード エディターには、XML スキーマで定義された要素の単語の入力候補を提供している XML 用の IntelliSense 機能が含まれています。 XML スキーマ定義 (XSD) ファイルをプロジェクトに追加しを使用して、スキーマのターゲット名前空間をインポートするかどうか、`Imports`ステートメント、コード エディターに要素を含める XSD スキーマから有効なメンバー変数の IntelliSense リスト<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 次の図の IntelliSense のメンバーを一覧表示、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
 ![Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")  
XML IntelliSense  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a>Visual Basic における XML IntelliSense を有効にします。  
 Visual Basic における XML IntelliSense を有効にするのには、Visual Basic プロジェクトで XSD スキーマ ファイルを含める必要があります。 使用して、コード ファイルに XSD スキーマのターゲット名前空間をインポートする必要がありますも、`Imports`ステートメントです。 使用して、プロジェクト レベルの名前空間の一覧にターゲットの名前空間を追加することができます、**参照**Visual Basic プロジェクト デザイナーのページです。 例については、次を参照してください。[方法: Visual Basic における XML IntelliSense を有効にする](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)です。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)と[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。  
  
 既定で、メモは、Visual Basic プロジェクトでの XSD スキーマ ファイルを参照してくださいことはできません。 をクリックする必要があります、 **[すべてのファイル**をプロジェクトに追加する XSD ファイルを選択する] ボタンをクリックします。  
  
### <a name="generating-a-schema-file-schema-inference"></a>スキーマ ファイル (スキーマの推論) を生成します。  
 既存の XML ファイルの XSD スキーマを作成するには、Visual Studio の XML ツールを使用して、XSD スキーマを推論します。  
  
-   SP1 以降、1 つまたは複数の XML ドキュメントから推論される XML スキーマ セットを作成し、プロジェクトが含まれる XML to Schema ウィザードを使用できます。 HTTP インターネット アドレスからの XML または型指定された、または XML to Schema ウィザードに貼り付ける XML テキスト ファイルの形式で XML ドキュメントの任意の組み合わせを使用することができます。 XML to Schema ウィザードにアクセスする をクリックして**新しい項目の追加**上、**プロジェクト**メニューを追加し、 **XML スキーマを**いずれかのテンプレート、**データ**または**の一般的な項目**テンプレート グループです。 XML スキーマ セットを推論するすべての XML ドキュメントのソースを追加したら、以下の をクリックして**OK**推論されるスキーマを作成するに設定します。 詳細については、次を参照してください。 [XML to Schema ウィザード](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)します。  
  
-   また、セットを XML ファイルから XSD スキーマを推論するのに Visual Studio XML エディターを使用することができます。 XML エディターを使用して設定 XML スキーマを作成するには、Visual Studio XML デザイナーで XML ファイルを開くクリックして**Create Schema**で、 **XML**メニュー。 XSD スキーマのセットを作成した後は、作成されたスキーマ セットを&1; つまたは複数の XSD ファイルに保存し、プロジェクトに追加できます。 詳細については、次を参照してください。[方法: Visual Basic における XML IntelliSense を有効にする](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)です。  
  
 別の XSD スキーマのセットが同じスキーマを使用するためのものでは複数の XML ドキュメントから推論される場合ことに注意してください。 これは、1 つの XML ファイルでは、特定の要素と属性が見つかったときに、または要素が次に例を異なる順序で含まれる場合に発生することができます。 XSD スキーマの推論を使用する場合は、完全性と精度の推定の XSD スキーマのセットを確認してください。  
  
## <a name="member-list"></a>メンバーの一覧  
 インスタンスを区切るためにピリオド (.) を入力し終わったら、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト (またはインスタンスの`IEnumerable(Of XElement)`または`IEnumerable(Of XDocument)`)、Visual Basic の IntelliSense が可能なオブジェクトのメンバーの一覧を表示します</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 最初のリストには、次の一覧に示すように XML 軸プロパティを表す&3; つのオプションが含まれます。  
  
|オプション|説明|  
|---|---|  
|**\< >**|要素の使用可能な子の一覧を表示するには、このオプションを選択します。 詳細については、次を参照してください[XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と<xref:System.Xml.Linq.XContainer.Elements%2A>メソッド。</xref:System.Xml.Linq.XContainer.Elements%2A> 。|  
|**@**|使用可能な属性の一覧を表示するには、このオプションを選択します。 詳細については、次を参照してください。 [XML 軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)します。このオプションは<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>の種類のオブジェクトに対してのみ使用できます。|  
|**…\< >**|可能性のある子孫要素の一覧を表示するには、このオプションを選択します。 詳細については、次を参照してください[方法: XML 子孫要素にアクセス](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)と<xref:System.Xml.Linq.XContainer.Elements%2A>メソッド。</xref:System.Xml.Linq.XContainer.Elements%2A> 。|  
  
 選択するか、一覧から XML オプションのいずれかの入力を開始します。 選択したオプションに固有の XML スキーマからの潜在的なメンバー、メンバーの一覧が表示されます。 ある場合は、XML 名前空間をインポート、特定の XML 名前空間プレフィックスに関連付けられている場合は、メンバーの一覧で、潜在的な XML 名前空間プレフィックスのリストが含まれています。  
  
 たとえば、次の XSD スキーマを検討してください。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"   
           elementFormDefault="qualified"   
           targetNamespace="http://SamplePurchaseOrder"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="PurchaseOrders">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="PurchaseOrder">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Address" />  
              <xs:element name="Items" />  
              <xs:element name="Comment" />  
            </xs:sequence>  
            <xs:attribute name="PurchaseOrderNumber" type="xs:unsignedShort" use="required" />  
            <xs:attribute name="OrderDate" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 XSD スキーマで有効な XML は、次のようになります。  
  
```  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 この XSD スキーマ ファイルをプロジェクトに含めるコード ファイルまたはプロジェクトに XSD スキーマからターゲットの名前空間をインポートすると、Visual Basic の IntelliSense は、Visual Basic コードを入力すると、スキーマからのメンバーを表示します。 XSD スキーマのターゲット名前空間が既定の名前空間としてインポートし、次を入力すると、使用可能な子要素の一覧が表示され、 `PurchaseOrder` XML 要素です。  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 一覧は、アドレス、コメント、および項目要素で構成されます。  
  
### <a name="certainty-levels-for-intellisense-list-items"></a>IntelliSense リスト項目のための確実性レベル  
 IntelliSense で使用する XSD の種類の決定は正確ではありません。 その結果、XML IntelliSense は多くの場合、可能なメンバーの一覧を展開を表示します。 IntelliSense のメンバーの一覧から項目を選択するために役立つ、項目には XML IntelliSense は、特定のメンバーが含まれる確実性のレベルを示す値が表示されます。  
  
 場合によって XML IntelliSense では、XSD スキーマから特定の種類を識別できます。 このような場合は、高度な確実性で使用可能な子要素、属性、またはその XSD 型の子孫要素が表示されます。 これらの項目は、チェック マークが付いた識別されます。  
  
 ただし、場合によって XML IntelliSense は XSD スキーマから特定の種類を識別することではありません。 このような場合は、使用可能な子要素、属性、またはプロジェクトの XSD スキーマからの子孫の要素の一覧を展開確実性の低いレベルで表示されます。 これらの項目は、疑問符 () で識別されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Basic における XML IntelliSense を有効にします。](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [XML to Schema ウィザード](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [XML 子孫軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)
