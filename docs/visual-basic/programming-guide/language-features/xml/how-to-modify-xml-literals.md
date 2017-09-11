---
title: "方法: XML リテラル (Visual Basic) の変更 |Microsoft ドキュメント"
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
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c21ded9fdd8f49b469b9a712be304c0d4cabb8c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="08551-102">方法 : XML リテラルを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08551-102">How to: Modify XML Literals (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="08551-103">XML リテラルを変更する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="08551-103"> provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="08551-104">リストにログインを追加したり、要素や属性を削除し、新しい XML 要素を持つ既存の要素を置換することもできます。</span><span class="sxs-lookup"><span data-stu-id="08551-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="08551-105">このトピックでは、既存の XML リテラルを変更する方法の例をいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="08551-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="08551-106">XML リテラルの値を変更するには</span><span class="sxs-lookup"><span data-stu-id="08551-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="08551-107">XML リテラルの値を変更するには、XML リテラルと設定への参照を取得、`Value`プロパティを目的の値にします。</span><span class="sxs-lookup"><span data-stu-id="08551-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="08551-108">次のコード例は、すべての値を更新、\<価格 > XML ドキュメント内の要素。</span><span class="sxs-lookup"><span data-stu-id="08551-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     <span data-ttu-id="08551-109">[!code-vb[VbXmlSamples2&4;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="08551-109">[!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="08551-110">次の XML のサンプルのソースを示していて、このコード例から XML を変更します。</span><span class="sxs-lookup"><span data-stu-id="08551-110">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>47.20</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>48.25</Price>  
      </Book>  
    </Catalog>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="08551-111">`Value`プロパティは、コレクション内の最初の XML 要素を参照します。</span><span class="sxs-lookup"><span data-stu-id="08551-111">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="08551-112">複数のコレクションで同じ名前を持つ要素がある場合は、設定、`Value`プロパティは、コレクション内の最初の要素だけに影響します。</span><span class="sxs-lookup"><span data-stu-id="08551-112">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="08551-113">XML リテラルに属性を追加するには</span><span class="sxs-lookup"><span data-stu-id="08551-113">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="08551-114">XML リテラルに属性を追加するには、XML リテラルへの参照を最初に取得します。</span><span class="sxs-lookup"><span data-stu-id="08551-114">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="08551-115">新しい XML 属性軸プロパティを追加することで、属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="08551-115">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="08551-116">追加することも、新しい<xref:System.Xml.Linq.XAttribute>オブジェクトを XML リテラルを使用して、<xref:System.Xml.Linq.XContainer.Add%2A>メソッド</xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="08551-116">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="08551-117">次の例では、両方のオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="08551-117">The following example shows both options.</span></span>  
  
     <span data-ttu-id="08551-118">[!code-vb[VbXmlSamples&#2;5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="08551-118">[!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="08551-119">次の XML のサンプルのソースを示していて、このコード例から XML を変更します。</span><span class="sxs-lookup"><span data-stu-id="08551-119">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
    ```  
  
     <span data-ttu-id="08551-120">XML 属性軸プロパティの詳細については、次を参照してください。 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)します。</span><span class="sxs-lookup"><span data-stu-id="08551-120">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="08551-121">XML リテラルに要素を追加するには</span><span class="sxs-lookup"><span data-stu-id="08551-121">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="08551-122">XML リテラルに要素を追加するには、XML リテラルへの参照を最初に取得します。</span><span class="sxs-lookup"><span data-stu-id="08551-122">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="08551-123">新しく追加できます<xref:System.Xml.Linq.XElement>オブジェクトを使用して要素の最後のサブ要素として、<xref:System.Xml.Linq.XContainer.Add%2A>メソッド</xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08551-123">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="08551-124">新しいを追加する<xref:System.Xml.Linq.XElement>オブジェクトを使用して最初のサブ要素として、<xref:System.Xml.Linq.XContainer.AddFirst%2A>メソッド</xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08551-124">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="08551-125">その他のサブ要素を基準とした特定の場所に新しい要素を追加するには、隣接するサブ要素への参照を最初に取得します。</span><span class="sxs-lookup"><span data-stu-id="08551-125">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="08551-126">新しいできますし、追加<xref:System.Xml.Linq.XElement>オブジェクトを使用して、隣接するサブ要素の前に、<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>メソッド</xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08551-126">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="08551-127">追加することも、新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して、隣接するサブ要素の後に、<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>メソッド</xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08551-127">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="08551-128">次の例では、これらの各手法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="08551-128">The following example shows examples of each of these techniques.</span></span>  
  
     <span data-ttu-id="08551-129">[!code-vb[VbXmlSamples2&6;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="08551-129">[!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="08551-130">次の XML のサンプルのソースを示していて、このコード例から XML を変更します。</span><span class="sxs-lookup"><span data-stu-id="08551-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331">  
        <Publisher>Microsoft Press</Publisher>  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <PublishDate>2005-2-14</PublishDate>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
    ```  
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="08551-131">XML リテラルから要素または属性を削除するには</span><span class="sxs-lookup"><span data-stu-id="08551-131">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="08551-132">XML リテラルから要素または属性を削除するには、要素または属性および呼び出しへの参照を取得、`Remove`メソッドを次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="08551-132">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     <span data-ttu-id="08551-133">[!code-vb[VbXmlSamples&#2;7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="08551-133">[!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span></span>  
  
     <span data-ttu-id="08551-134">次の XML のサンプルのソースを示していて、このコード例から XML を変更します。</span><span class="sxs-lookup"><span data-stu-id="08551-134">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book></Catalog>  
    ```  
  
     <span data-ttu-id="08551-135">XML リテラルからすべての要素または属性を削除するには、XML リテラルへの参照を取得およびを呼び出す、<xref:System.Xml.Linq.XElement.RemoveAll%2A>メソッド</xref:System.Xml.Linq.XElement.RemoveAll%2A>。</span><span class="sxs-lookup"><span data-stu-id="08551-135">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="08551-136">XML リテラルを変更するには</span><span class="sxs-lookup"><span data-stu-id="08551-136">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="08551-137">XML 要素の名前を変更するには、まず要素への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="08551-137">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="08551-138">できますし、新規に作成する<xref:System.Xml.Linq.XElement>オブジェクトを持つ新しい名前を指定し、新しい渡す<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XNode.ReplaceWith%2A>、既存のメソッド<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08551-138">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="08551-139">ものに交換する要素に保存する必要があるサブ要素がある場合は、新しい値を設定<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XContainer.Nodes%2A>は既存の要素のプロパティ</xref:System.Xml.Linq.XContainer.Nodes%2A></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08551-139">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="08551-140">これにより、既存の要素の内部 XML を新しい要素の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="08551-140">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="08551-141">それ以外の場合に新しい要素の値を設定することができます、`Value`は既存の要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="08551-141">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="08551-142">次のコード例では、すべて置き換えられます\<説明 > を持つ要素が\<抽象 > 要素。</span><span class="sxs-lookup"><span data-stu-id="08551-142">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="08551-143">内容、\<説明 > 要素は、新しい保持\<抽象 > 要素を使用して、<xref:System.Xml.Linq.XContainer.Nodes%2A>のプロパティ、\<説明 ><xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XContainer.Nodes%2A>。</span><span class="sxs-lookup"><span data-stu-id="08551-143">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="08551-144">[!code-vb[VbXmlSamples&#2;8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="08551-144">[!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span></span>  
  
     <span data-ttu-id="08551-145">次の XML のサンプルのソースを示していて、このコード例から XML を変更します。</span><span class="sxs-lookup"><span data-stu-id="08551-145">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
        <Description>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Description>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <Description>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Description>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>    <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>    <Abstract>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Abstract>  
      </Book>  
    </Catalog>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="08551-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="08551-146">See Also</span></span>  
 <span data-ttu-id="08551-147">[Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="08551-147">[Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="08551-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="08551-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="08551-149"> [方法: ファイル、文字列またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="08551-149"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="08551-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="08551-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="08551-151"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="08551-151"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
