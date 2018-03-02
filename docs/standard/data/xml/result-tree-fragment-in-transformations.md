---
title: "変換での結果ツリー フラグメントの処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04e23f39f522fca7f69aa86be7036320a5698a60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="f6cc4-102">変換での結果ツリー フラグメントの処理</span><span class="sxs-lookup"><span data-stu-id="f6cc4-102">Result Tree Fragment in Transformations</span></span>
> [!NOTE]
>  <span data-ttu-id="f6cc4-103"><xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="f6cc4-104"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f6cc4-105">詳細については、「[XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)」と「[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f6cc4-106">結果ツリー フラグメントは、ノード セットの特殊な型にすぎません。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="f6cc4-107">ノード フラグメントでは、ノード セットで実行できる任意の関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="f6cc4-108">`node-set()` 関数を使用して結果ツリー フラグメントをノード セットに変換し、ノード セットを使用できる任意の場所でそれを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>  
  
 <span data-ttu-id="f6cc4-109">結果ツリー フラグメントは、スタイル シートで `<xsl:variable>` 要素または `<xsl:param>` 要素を特定の方法で使用した結果として作成されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="f6cc4-110">`variable` 要素と `parameter` 要素の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 <span data-ttu-id="f6cc4-111">`parameter` 要素では、いくつかの方法で修飾名 (`Qname`) に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="f6cc4-112">パラメーターに既定値を割り当てるには、`select` 属性の XPath (XML Path Language) 式から内容を返すか、テンプレート本体の内容をパラメーターに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="f6cc4-113">`variable` 要素でも、いくつかの方法で値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="f6cc4-114">`select` 属性の XPath 式から内容を返すか、テンプレート本体の内容を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="f6cc4-115">`parameter` 要素でも `variable` 要素でも、XPath 式で値を割り当てた場合は、4 つの基本 XPath 型であるブール値、文字列、数値、ノード セットのうちのいずれかが返されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="f6cc4-116">テンプレート本体で値を指定した場合は、XPath 型でないデータ型である結果ツリー フラグメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>  
  
 <span data-ttu-id="f6cc4-117">変数が、4 つの基本 XPath データ型のうちの 1 つではなく、結果ツリー フラグメントに関連付けられたときにだけ、XPath クエリからは 4 つの基本 XPath オブジェクト型以外の型が返されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="f6cc4-118">結果ツリー フラグメントとその動作については、W3C (World Wide Web Consortium) 仕様 (http://www.w3.org/XSLT) のセクション 11.1「Result Tree Fragments」からセクション 11.6「Passing Parameters to Templates」に記述されています。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-118">Result tree fragments and their behavior are discussed in the World Wide Web Consortium (W3C) specification at www.w3.org/XSLT, section 11.1 Result Tree Fragments through section 11.6 Passing Parameters to Templates.</span></span> <span data-ttu-id="f6cc4-119">セクション 1「Introduction」でも、結果ツリー フラグメントを返したり結果ツリー フラグメントを作成したりする XSLT 名前空間の要素をテンプレートに含める方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-119">Also, section 1 Introduction discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>  
  
 <span data-ttu-id="f6cc4-120">結果ツリー フラグメントは、概念的には、1 つのルート ノードだけを持つノード セットと同じ動作をします。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="f6cc4-121">ただし、返されるその他のノードは子ノードになります。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="f6cc4-122">プログラムで子ノードを参照するには、`<xsl:copy-of>` 要素を使用して結果ツリー フラグメントを結果ツリーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="f6cc4-123">copy-of を実行すると、すべての子ノードも結果ツリーに順番にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="f6cc4-124">`copy` または `copy-of` を使用するまで、結果ツリー フラグメントは、結果ツリーの一部や変換の出力の一部にはなりません。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>  
  
 <span data-ttu-id="f6cc4-125">結果ツリー フラグメントの返されたノードを反復処理するには、<xref:System.Xml.XPath.XPathNavigator> を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="f6cc4-126">XML を含む `fragment` パラメーターを指定して関数を呼び出すことにより、スタイル シート内で結果ツリー フラグメントを作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:var name="fragment">  
        <node1>  
            <node2/>  
        </node1>  
    <xsl:var>  
  
  <msxsl:script language="C#" implements-prefix="user">  
    function NodeFragment(XPathNavigator nav)  
    {  
      if (nav.HasSelection == false)  
        XPathNavigator.MoveToNext();  
      return;  
    }  
  </msxsl:script>  
  
    <xsl:template match="/">  
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="f6cc4-127">結果ツリー フラグメントの一種である RTF (Rich Text Format) 形式の変数がノード セットに変換されない例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="f6cc4-128">この場合、変数はスクリプト関数に渡され、ノード間の移動には <xref:System.Xml.XPath.XPathNavigator> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNavigator nav)  
    {  
        bool b = nav.MoveToFirstChild();  
        if (b)  
            return nav.Value;  
        else  
            return "Does not exist";  
    }  
  
]]>  
  
</msxsl:script>  
  
<xsl:template match="/">  
    <first_book>  
        <xsl:value-of select="user:func($node-fragment)"/>  
    </first_book>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="f6cc4-129">このスタイル シートを使用して XML を変換した結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f6cc4-130">出力</span><span class="sxs-lookup"><span data-stu-id="f6cc4-130">Output</span></span>  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 <span data-ttu-id="f6cc4-131">上で説明したように、`node-set` 関数を使用すると、結果ツリー フラグメントをノード セットに変換できます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="f6cc4-132">結果として得られるノードには、ツリーのルート ノードである単一のノードが常に含まれます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="f6cc4-133">結果ツリー フラグメントから変換したノード セットは、for-each ステートメントや `select` 属性の値など、標準ノード セットを使用できる任意の場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="f6cc4-134">フラグメントをノード セットに変換し、ノード セットとして使用するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 <span data-ttu-id="f6cc4-135">フラグメントをノード セットに変換した後は、ノード間の移動に <xref:System.Xml.XPath.XPathNavigator> を使用しません。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="f6cc4-136">ノード セットでは、<xref:System.Xml.XPath.XPathNodeIterator> を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>  
  
 <span data-ttu-id="f6cc4-137">`$var` という変数がスタイル シート内のノード ツリーである例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="f6cc4-138">for-each ステートメントを `node-set` 関数と組み合わせて使用すると、このツリーをノード セットとして反復処理できます。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:variable name="states">  
        <node1>AL</node1>  
        <node1>CA</node1>  
        <node1>CO</node1>  
        <node1>WA</node1>  
    </xsl:variable>  
  
    <xsl:template match="/">  
            <xsl:for-each select="msxsl:node-set($states)"/>   
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="f6cc4-139">次の例も、結果ツリー フラグメントの一種である RTF 形式の変数ですが、この場合は、変数をノード セットに変換した後、XPathNodeIterator としてスクリプト関数に渡しています。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNodeIterator it)  
    {  
        it.MoveNext();   
        return it.Current.Value;   
        //it.Current returns XPathNavigator positioned on the current node  
    }  
  
]]>  
  
</msxsl:script>  
<xsl:template match="/">  
    <books>  
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>  
    </books>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="f6cc4-140">このスタイル シートを使用して XML を変換した結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6cc4-140">The following is the result of transforming XML with this style sheet:</span></span>  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6cc4-141">参照</span><span class="sxs-lookup"><span data-stu-id="f6cc4-141">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="f6cc4-142">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="f6cc4-142">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="f6cc4-143">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="f6cc4-143">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
