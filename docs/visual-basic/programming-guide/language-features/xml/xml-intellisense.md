---
title: "XML IntelliSense in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, XML"
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# XML IntelliSense in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic コード エディターには、XML スキーマで定義されている要素の単語入力を補完する、XML 用の IntelliSense 機能が付属しています。  XML スキーマ定義 \(XSD: XML Schema Definition\) ファイルをプロジェクトに追加し、スキーマの対象名前空間を `Imports` ステートメントを使用してインポートすると、コード エディターによって、XSD スキーマの要素が、<xref:System.Xml.Linq.XElement> オブジェクトと <xref:System.Xml.Linq.XDocument> オブジェクト用の IntelliSense 有効メンバー変数リストに取り込まれます。  <xref:System.Xml.Linq.XElement> オブジェクト用の IntelliSense メンバー リストを次に示します。  
  
 ![Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/media/xml-intellisense.png "XML\_Intellisense")  
XML IntelliSense  
  
## Visual Basic での XML IntelliSense の有効化  
 Visual Basic で XML IntelliSense を有効にするには、XSD スキーマ ファイルを Visual Basic プロジェクトに追加する必要があります。  また、XSD スキーマの対象名前空間を `Imports` ステートメントを使用してコード ファイルにインポートする必要があります。  また、Visual Basic プロジェクト デザイナーの **\[参照\]** ページを使用して、プロジェクト レベルの名前空間リストにスキーマの名前空間を追加することもできます。  例については、「[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)」を参照してください。  詳細については、「[Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)」および「[\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)」を参照してください。  
  
 既定では、Visual Basic プロジェクトの XSD スキーマ ファイルは表示されません。  プロジェクトに追加する XSD ファイルを選択するには、**\[すべてのファイルを表示\]** ボタンをクリックすることが必要な場合があります。  
  
### スキーマ ファイルの生成 \(スキーマの推論\)  
 Visual Studio の XML ツールを使用して XSD スキーマを推論することにより、既存の XML ファイル用の XSD スキーマを作成できます。  
  
-   SP1 より、XML to Schema ウィザードを使用して、1 つ以上の XML ドキュメントから推論される XML スキーマ セットを作成し、プロジェクトに追加できるようになりました。  テキスト ファイル形式の XML ドキュメント、HTTP インターネット アドレスからの XML、および XML to Schema ウィザードに入力するか貼り付ける XML を任意に組み合わせて使用できます。  XML to Schema ウィザードにアクセスするには、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックし、**\[データ\]** と **\[共通項目\]** のいずれかのテンプレート グループから **XML to Schema** テンプレートを追加します。  XML スキーマ セットを推論する対象の XML ドキュメント ソースをすべて追加したら、**\[OK\]** をクリックして推論されるスキーマ セットを作成します。  詳細については、「[XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)」を参照してください。  
  
-   Visual Studio XML エディターを使用して XML ファイルから XSD スキーマ セットを推論することもできます。  XML エディターを使用して XML スキーマ セットを作成するには、Visual Studio の XML デザイナーで XML ファイルを開き、**\[XML\]** メニューの **\[スキーマの作成\]** をクリックします。  作成した XSD スキーマ セットは、1 つ以上の XSD ファイルに保存し、プロジェクトに追加できます。  詳細については、「[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)」を参照してください。  
  
 スキーマが同じである必要のある複数の XML ドキュメントから、複数の異なる XSD スキーマ セットが推論される場合があることに注意してください。  このようなことは、特定の要素と属性がいずれかの XML だけに存在したり、含まれている要素の順序が異なっていたりする場合に、発生する可能性があります。  XSD スキーマの推論を使用するときは、推論された XSD スキーマ セットが完全で正確であることを確認する必要があります。  
  
## メンバー リスト  
 ピリオド \(.\) を入力して <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XDocument> オブジェクトのインスタンスか、`IEnumerable(Of XElement)` または `IEnumerable(Of XDocument)` のインスタンスを区切ると、Visual Basic IntelliSense によって、使用可能なオブジェクト メンバーの一覧が表示されます。  この初期リストには、次に示す XML 軸プロパティを表す 3 つのオプションが含まれます。  
  
|||  
|-|-|  
|オプション|Description|  
|**\< \>**|使用可能な子要素の一覧を表示するには、このオプションを選択します。  詳細については、[XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) メソッドと <xref:System.Xml.Linq.XContainer.Elements%2A> メソッドを参照してください。|  
|**@**|使用可能な属性の一覧を表示するには、このオプションを選択します。  詳細については、「[XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)」を参照してください。このオプションは、<xref:System.Xml.Linq.XElement> 型のオブジェクトに対してのみ使用できます。|  
|**…\< \>**|使用可能な子孫要素の一覧を表示するには、このオプションを選択します。  詳細については、[How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) メソッドと <xref:System.Xml.Linq.XContainer.Elements%2A> メソッドを参照してください。|  
  
 一覧から任意の XML オプションを選択するか、入力を開始します。  選択したオプションに固有の XML スキーマのメンバーで、使用可能なメンバーが、メンバー リストに表示されます。  特定の XML 名前空間プレフィックスに関連付けられた XML 名前空間をインポートしている場合は、使用可能な XML 名前空間プレフィックスの一覧もメンバー リストに表示されます。  
  
 たとえば、次のような XSD スキーマがあるとします。  
  
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
  
 この XSD スキーマで有効な XML は次のようになります。  
  
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
  
 この XSD スキーマ ファイルをプロジェクトに追加し、スキーマの対象名前空間を XSD スキーマからコード ファイルまたはプロジェクトにインポートすると、Visual Basic コードの入力時に、Visual Basic IntelliSense によって、このスキーマのメンバーが表示されます。  XSD スキーマの対象名前空間を既定の名前空間としてインポートし、次のように入力すると、IntelliSense によって、`PurchaseOrder` XML 要素の使用可能な子要素の一覧が表示されます。  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 この一覧は、Address、Comment、および Items の各要素で構成されます。  
  
### IntelliSense リスト項目の確実性のレベル  
 IntelliSense で使用する XSD 型の判別は厳密ではありません。  その結果として、XML IntelliSense では多くの場合、使用可能なメンバーを示す展開されたリストが表示されます。  IntelliSense メンバー リストから項目を選択しやすくするために、項目は、XML IntelliSense で特定のメンバーに割り当てられている確実性のレベルを示すインジケーターと共に表示されます。  
  
 XML IntelliSense は、XSD スキーマの特定の型を識別できる場合があります。  そのような場合、その XSD 型で使用できる高い確実性がある子要素、属性、または子孫要素が表示されます。  これらの項目は、チェック マークによって識別されます。  
  
 ただし、XML IntelliSense は、XSD スキーマの特定の型を識別できない場合もあります。  そのような場合、プロジェクトで使用できる確実性の低い XSD スキーマの子要素、属性、または子孫要素を示す展開されたリストが表示されます。  これらの項目は、疑問符によって識別されます。  
  
## 参照  
 [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)