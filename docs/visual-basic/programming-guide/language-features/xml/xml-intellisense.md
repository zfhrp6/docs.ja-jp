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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 9a3c6f923bc9458997c388d4cf74ca113265a8cc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017

---
# <a name="xml-intellisense-in-visual-basic"></a><span data-ttu-id="934f0-102">Visual Basic における XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="934f0-102">XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="934f0-103">Visual Basic コード エディターには、XML スキーマで定義された要素の単語の入力候補を提供している XML 用の IntelliSense 機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="934f0-103">The Visual Basic Code Editor includes IntelliSense features for XML that provide word completion for elements defined in an XML schema.</span></span> <span data-ttu-id="934f0-104">XML スキーマ定義 (XSD) ファイルをプロジェクトに追加しを使用して、スキーマのターゲット名前空間をインポートするかどうか、`Imports`ステートメント、コード エディターに要素を含める XSD スキーマから有効なメンバー変数の IntelliSense リスト<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="934f0-104">If you include an XML Schema Definition (XSD) file in your project and import the target namespace of the schema by using the `Imports` statement, the Code Editor will include elements from the XSD schema in the IntelliSense list of valid member variables for <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="934f0-105">次の図の IntelliSense のメンバーを一覧表示、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="934f0-105">The following illustration shows the IntelliSense members list for an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="934f0-106">![Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span><span class="sxs-lookup"><span data-stu-id="934f0-106">![XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span></span>  
<span data-ttu-id="934f0-107">XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="934f0-107">XML IntelliSense</span></span>  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a><span data-ttu-id="934f0-108">Visual Basic における XML IntelliSense を有効にします。</span><span class="sxs-lookup"><span data-stu-id="934f0-108">Enabling XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="934f0-109">Visual Basic における XML IntelliSense を有効にするのには、Visual Basic プロジェクトで XSD スキーマ ファイルを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="934f0-109">To enable XML IntelliSense in Visual Basic, you must include an XSD schema file in your Visual Basic project.</span></span> <span data-ttu-id="934f0-110">使用して、コード ファイルに XSD スキーマのターゲット名前空間をインポートする必要がありますも、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="934f0-110">You must also import the target namespace for the XSD schema into your code file by using the `Imports` statement.</span></span> <span data-ttu-id="934f0-111">使用して、プロジェクト レベルの名前空間の一覧にターゲットの名前空間を追加することができます、**参照**Visual Basic プロジェクト デザイナーのページです。</span><span class="sxs-lookup"><span data-stu-id="934f0-111">Alternatively, you can add the target namespace to the project-level namespace list by using the **References** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="934f0-112">例については、次を参照してください。[方法: Visual Basic における XML IntelliSense を有効にする](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)です。</span><span class="sxs-lookup"><span data-stu-id="934f0-112">For examples, see [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span> <span data-ttu-id="934f0-113">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)と[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="934f0-113">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) and [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="934f0-114">既定で、メモは、Visual Basic プロジェクトでの XSD スキーマ ファイルを参照してくださいことはできません。</span><span class="sxs-lookup"><span data-stu-id="934f0-114">Note that by default you cannot see XSD schema files in Visual Basic projects.</span></span> <span data-ttu-id="934f0-115">をクリックする必要があります、 **[すべてのファイル**をプロジェクトに追加する XSD ファイルを選択する] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="934f0-115">You may have to click the **Show All Files** button to select an XSD file to include in your project.</span></span>  
  
### <a name="generating-a-schema-file-schema-inference"></a><span data-ttu-id="934f0-116">スキーマ ファイル (スキーマの推論) を生成します。</span><span class="sxs-lookup"><span data-stu-id="934f0-116">Generating a Schema File (Schema Inference)</span></span>  
 <span data-ttu-id="934f0-117">既存の XML ファイルの XSD スキーマを作成するには、Visual Studio の XML ツールを使用して、XSD スキーマを推論します。</span><span class="sxs-lookup"><span data-stu-id="934f0-117">You can create an XSD schema for an existing XML file by inferring the XSD schema by using Visual Studio XML tools.</span></span>  
  
-   <span data-ttu-id="934f0-118">SP1 以降、1 つまたは複数の XML ドキュメントから推論される XML スキーマ セットを作成し、プロジェクトが含まれる XML to Schema ウィザードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="934f0-118">Starting in SP1, you can use the XML to Schema Wizard to create an XML Schema set that is inferred from one or more XML documents and include it your project.</span></span> <span data-ttu-id="934f0-119">HTTP インターネット アドレスからの XML または型指定された、または XML to Schema ウィザードに貼り付ける XML テキスト ファイルの形式で XML ドキュメントの任意の組み合わせを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="934f0-119">You can use any combination of XML documents in the form of text files, XML from HTTP Internet addresses, or XML that is typed or pasted into the XML to Schema Wizard.</span></span> <span data-ttu-id="934f0-120">XML to Schema ウィザードにアクセスする をクリックして**新しい項目の追加**上、**プロジェクト**メニューを追加し、 **XML スキーマを**いずれかのテンプレート、**データ**または**の一般的な項目**テンプレート グループです。</span><span class="sxs-lookup"><span data-stu-id="934f0-120">To access the XML to Schema Wizard, click **Add New Item** on the **Project** menu and add an **XML to Schema** template from either the **Data** or **Common Items** template group.</span></span> <span data-ttu-id="934f0-121">XML スキーマ セットを推論するすべての XML ドキュメントのソースを追加したら、以下の をクリックして**OK**推論されるスキーマを作成するに設定します。</span><span class="sxs-lookup"><span data-stu-id="934f0-121">After you have included all the XML document sources to infer the XML Schema set from, click **OK** to create the inferred schema set.</span></span> <span data-ttu-id="934f0-122">詳細については、次を参照してください。 [XML to Schema ウィザード](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)します。</span><span class="sxs-lookup"><span data-stu-id="934f0-122">For more information, see [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).</span></span>  
  
-   <span data-ttu-id="934f0-123">また、セットを XML ファイルから XSD スキーマを推論するのに Visual Studio XML エディターを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="934f0-123">You can also use the Visual Studio XML Editor to infer an XSD schema set from an XML file.</span></span> <span data-ttu-id="934f0-124">XML エディターを使用して設定 XML スキーマを作成するには、Visual Studio XML デザイナーで XML ファイルを開くクリックして**Create Schema**で、 **XML**メニュー。</span><span class="sxs-lookup"><span data-stu-id="934f0-124">To create an XML schema set by using the XML Editor, open an XML file in the Visual Studio XML Designer and then click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="934f0-125">XSD スキーマのセットを作成した後は、作成されたスキーマ セットを&1; つまたは複数の XSD ファイルに保存し、プロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="934f0-125">After you create the XSD schema set, you can save the created schema set to one or more XSD files and include them in your project.</span></span> <span data-ttu-id="934f0-126">詳細については、次を参照してください。[方法: Visual Basic における XML IntelliSense を有効にする](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)です。</span><span class="sxs-lookup"><span data-stu-id="934f0-126">For more information, see[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span>  
  
 <span data-ttu-id="934f0-127">別の XSD スキーマのセットが同じスキーマを使用するためのものでは複数の XML ドキュメントから推論される場合ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="934f0-127">Note that different XSD schema sets might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="934f0-128">これは、1 つの XML ファイルでは、特定の要素と属性が見つかったときに、または要素が次に例を異なる順序で含まれる場合に発生することができます。</span><span class="sxs-lookup"><span data-stu-id="934f0-128">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="934f0-129">XSD スキーマの推論を使用する場合は、完全性と精度の推定の XSD スキーマのセットを確認してください。</span><span class="sxs-lookup"><span data-stu-id="934f0-129">You should review inferred XSD schema sets for completeness and accuracy when you use XSD schema inference.</span></span>  
  
## <a name="member-list"></a><span data-ttu-id="934f0-130">メンバーの一覧</span><span class="sxs-lookup"><span data-stu-id="934f0-130">Member List</span></span>  
 <span data-ttu-id="934f0-131">インスタンスを区切るためにピリオド (.) を入力し終わったら、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト (またはインスタンスの`IEnumerable(Of XElement)`または`IEnumerable(Of XDocument)`)、Visual Basic の IntelliSense が可能なオブジェクトのメンバーの一覧を表示します</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="934f0-131">After you type a period (.) to delimit an instance of an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object (or an instance of `IEnumerable(Of XElement)` or `IEnumerable(Of XDocument)`), Visual Basic IntelliSense displays a list of possible object members.</span></span> <span data-ttu-id="934f0-132">最初のリストには、次の一覧に示すように XML 軸プロパティを表す&3; つのオプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="934f0-132">The initial list includes three options that represent XML axis properties, as described in the following list.</span></span>  
  
|<span data-ttu-id="934f0-133">オプション</span><span class="sxs-lookup"><span data-stu-id="934f0-133">Option</span></span>|<span data-ttu-id="934f0-134">説明</span><span class="sxs-lookup"><span data-stu-id="934f0-134">Description</span></span>|  
|---|---|  
|**\< >**|<span data-ttu-id="934f0-135">要素の使用可能な子の一覧を表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="934f0-135">Select this option to show a list of possible child elements.</span></span> <span data-ttu-id="934f0-136">詳細については、次を参照してください[XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と<xref:System.Xml.Linq.XContainer.Elements%2A>メソッド。</xref:System.Xml.Linq.XContainer.Elements%2A> 。</span><span class="sxs-lookup"><span data-stu-id="934f0-136">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
|**@**|<span data-ttu-id="934f0-137">使用可能な属性の一覧を表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="934f0-137">Select this option to show a list of possible attributes.</span></span> <span data-ttu-id="934f0-138">詳細については、次を参照してください。 [XML 軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)します。このオプションは<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>の種類のオブジェクトに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="934f0-138">For more information, see [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).This option is available only for objects of type <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="934f0-139">**…\< >**</span><span class="sxs-lookup"><span data-stu-id="934f0-139">**…\< >**</span></span>|<span data-ttu-id="934f0-140">可能性のある子孫要素の一覧を表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="934f0-140">Select this option to show a list of possible descendant elements.</span></span> <span data-ttu-id="934f0-141">詳細については、次を参照してください[方法: XML 子孫要素にアクセス](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)と<xref:System.Xml.Linq.XContainer.Elements%2A>メソッド。</xref:System.Xml.Linq.XContainer.Elements%2A> 。</span><span class="sxs-lookup"><span data-stu-id="934f0-141">For more information, see [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
  
 <span data-ttu-id="934f0-142">選択するか、一覧から XML オプションのいずれかの入力を開始します。</span><span class="sxs-lookup"><span data-stu-id="934f0-142">Select or begin typing any of the XML options from the list.</span></span> <span data-ttu-id="934f0-143">選択したオプションに固有の XML スキーマからの潜在的なメンバー、メンバーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-143">The member list will then display potential members from the XML schema that are specific to the selected option.</span></span> <span data-ttu-id="934f0-144">ある場合は、XML 名前空間をインポート、特定の XML 名前空間プレフィックスに関連付けられている場合は、メンバーの一覧で、潜在的な XML 名前空間プレフィックスのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="934f0-144">If you have XML namespaces imported that are associated with a specific XML namespace prefix, a list of potential XML namespace prefixes is included in the member list.</span></span>  
  
 <span data-ttu-id="934f0-145">たとえば、次の XSD スキーマを検討してください。</span><span class="sxs-lookup"><span data-stu-id="934f0-145">For example, consider the following XSD schema.</span></span>  
  
```xml  
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
  
 <span data-ttu-id="934f0-146">XSD スキーマで有効な XML は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="934f0-146">Valid XML for the XSD schema would resemble the following.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 <span data-ttu-id="934f0-147">この XSD スキーマ ファイルをプロジェクトに含めるコード ファイルまたはプロジェクトに XSD スキーマからターゲットの名前空間をインポートすると、Visual Basic の IntelliSense は、Visual Basic コードを入力すると、スキーマからのメンバーを表示します。</span><span class="sxs-lookup"><span data-stu-id="934f0-147">If you include this XSD schema file in a project and import the target namespace from the XSD schema into your code file or project, Visual Basic IntelliSense displays members from the schema as you type your Visual Basic code.</span></span> <span data-ttu-id="934f0-148">XSD スキーマのターゲット名前空間が既定の名前空間としてインポートし、次を入力すると、使用可能な子要素の一覧が表示され、 `PurchaseOrder` XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="934f0-148">If the target namespace for the XSD schema is imported as the default namespace and you type the following, IntelliSense displays a list of possible child elements for the `PurchaseOrder` XML element.</span></span>  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 <span data-ttu-id="934f0-149">一覧は、アドレス、コメント、および項目要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-149">The list consists of the Address, Comment, and Items elements.</span></span>  
  
### <a name="certainty-levels-for-intellisense-list-items"></a><span data-ttu-id="934f0-150">IntelliSense リスト項目のための確実性レベル</span><span class="sxs-lookup"><span data-stu-id="934f0-150">Certainty Levels for IntelliSense List Items</span></span>  
 <span data-ttu-id="934f0-151">IntelliSense で使用する XSD の種類の決定は正確ではありません。</span><span class="sxs-lookup"><span data-stu-id="934f0-151">Determining the XSD type to use for IntelliSense is not exact.</span></span> <span data-ttu-id="934f0-152">その結果、XML IntelliSense は多くの場合、可能なメンバーの一覧を展開を表示します。</span><span class="sxs-lookup"><span data-stu-id="934f0-152">As a result, XML IntelliSense will often show an expanded list of possible members.</span></span> <span data-ttu-id="934f0-153">IntelliSense のメンバーの一覧から項目を選択するために役立つ、項目には XML IntelliSense は、特定のメンバーが含まれる確実性のレベルを示す値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-153">To aid you in selecting an item from the IntelliSense member list, items are displayed with an indication of the level of certainty that XML IntelliSense has for a particular member.</span></span>  
  
 <span data-ttu-id="934f0-154">場合によって XML IntelliSense では、XSD スキーマから特定の種類を識別できます。</span><span class="sxs-lookup"><span data-stu-id="934f0-154">Sometimes XML IntelliSense can identify a specific type from the XSD schema.</span></span> <span data-ttu-id="934f0-155">このような場合は、高度な確実性で使用可能な子要素、属性、またはその XSD 型の子孫要素が表示されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-155">In these cases, it will display possible child elements, attributes, or descendant elements for that XSD type with a high degree of certainty.</span></span> <span data-ttu-id="934f0-156">これらの項目は、チェック マークが付いた識別されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-156">These items are identified with a check mark.</span></span>  
  
 <span data-ttu-id="934f0-157">ただし、場合によって XML IntelliSense は XSD スキーマから特定の種類を識別することではありません。</span><span class="sxs-lookup"><span data-stu-id="934f0-157">However, sometimes XML IntelliSense is not able to identify a specific type from the XSD schema.</span></span> <span data-ttu-id="934f0-158">このような場合は、使用可能な子要素、属性、またはプロジェクトの XSD スキーマからの子孫の要素の一覧を展開確実性の低いレベルで表示されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-158">In these cases, it will display an expanded list of possible child elements, attributes, or descendant elements from the XSD schema for the project with a low degree of certainty.</span></span> <span data-ttu-id="934f0-159">これらの項目は、疑問符 () で識別されます。</span><span class="sxs-lookup"><span data-stu-id="934f0-159">These items are identified with a question mark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934f0-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="934f0-160">See Also</span></span>  
 <span data-ttu-id="934f0-161">[方法: Visual Basic における XML IntelliSense を有効にします。](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span><span class="sxs-lookup"><span data-stu-id="934f0-161">[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span></span>  
<span data-ttu-id="934f0-162"> [XML to Schema ウィザード](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="934f0-162"> [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span></span>  
<span data-ttu-id="934f0-163"> [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="934f0-163"> [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="934f0-164"> [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="934f0-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="934f0-165"> [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="934f0-165"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="934f0-166"> [XML 子孫軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="934f0-166"> [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span></span>  
<span data-ttu-id="934f0-167"> [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="934f0-167"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
