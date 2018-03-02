---
title: "オブジェクト階層の XML データへのマップ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2191cb15a85e9b16ff0a21084668e80d3c197bfa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="fa67d-102">オブジェクト階層の XML データへのマップ</span><span class="sxs-lookup"><span data-stu-id="fa67d-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="fa67d-103">メモリに読み込まれた XML ドキュメントは、ツリーという概念で表現されます。</span><span class="sxs-lookup"><span data-stu-id="fa67d-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="fa67d-104">プログラミングでは、オブジェクト階層を利用してツリーのノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="fa67d-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="fa67d-105">XML コンテンツがどのようにノードに変換されるかを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="fa67d-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="fa67d-106">XML が XML ドキュメント オブジェクト モデル (DOM) に読み込まれると、各部がノードに変換されます。これらのノードは、ノード型や値など、ノード自身に関する付加的なメタデータを保持しています。</span><span class="sxs-lookup"><span data-stu-id="fa67d-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="fa67d-107">ノード型はノードのオブジェクトであり、ノード型によって実行可能なアクションおよび設定や取得が可能なプロパティが決まります。</span><span class="sxs-lookup"><span data-stu-id="fa67d-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="fa67d-108">次のような簡単な XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fa67d-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="fa67d-109">**入力**</span><span class="sxs-lookup"><span data-stu-id="fa67d-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="fa67d-110">この入力は、メモリ上で次のようなノード ツリーとして表現され、ノード型プロパティが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fa67d-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="fa67d-111">![サンプル ノード ツリー](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="fa67d-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="fa67d-112">book と title のノード ツリー表現</span><span class="sxs-lookup"><span data-stu-id="fa67d-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="fa67d-113">`book` 要素は **XmlElement** オブジェクトになり、次の要素の `title` も **XmlElement** になりますが、要素コンテンツは **XmlText** オブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="fa67d-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="fa67d-114">**XmlElement** のメソッドとプロパティは、**XmlText** オブジェクトで使用できるメソッドとプロパティとは異なります。</span><span class="sxs-lookup"><span data-stu-id="fa67d-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="fa67d-115">実行可能なアクションはノード型によって決定されるため、XML マークアップがどのノード型になるかを理解することがきわめて重要です。</span><span class="sxs-lookup"><span data-stu-id="fa67d-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="fa67d-116">XML データを読み込み、ノード型に応じて異なるテキストを書き出す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fa67d-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="fa67d-117">入力として、次の **items.xml** という XML データ ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa67d-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="fa67d-118">**入力**</span><span class="sxs-lookup"><span data-stu-id="fa67d-118">**Input**</span></span>  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 <span data-ttu-id="fa67d-119">**items.xml** ファイルを読み込み、それぞれのノード型の情報を表示するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fa67d-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 <span data-ttu-id="fa67d-120">この例の出力を確認すると、データからノード型へのマップがわかります。</span><span class="sxs-lookup"><span data-stu-id="fa67d-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="fa67d-121">**出力**</span><span class="sxs-lookup"><span data-stu-id="fa67d-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="fa67d-122">入力と、コードから生成された出力を 1 行ずつ対比させた以下の表を見れば、どのノード テストによってどの出力行が生成されたのかを分析でき、どの XML データがどのノード型になったかがわかります。</span><span class="sxs-lookup"><span data-stu-id="fa67d-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="fa67d-123">入力</span><span class="sxs-lookup"><span data-stu-id="fa67d-123">Input</span></span>|<span data-ttu-id="fa67d-124">出力</span><span class="sxs-lookup"><span data-stu-id="fa67d-124">Output</span></span>|<span data-ttu-id="fa67d-125">ノード型のテスト</span><span class="sxs-lookup"><span data-stu-id="fa67d-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="fa67d-126">\<?xml version="1.0"?></span><span class="sxs-lookup"><span data-stu-id="fa67d-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="fa67d-127">\<?xml version='1.0'?></span><span class="sxs-lookup"><span data-stu-id="fa67d-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="fa67d-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="fa67d-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="fa67d-129">\<!-- This is a sample XML document --></span><span class="sxs-lookup"><span data-stu-id="fa67d-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="fa67d-130">\<!--This is a sample XML document --></span><span class="sxs-lookup"><span data-stu-id="fa67d-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="fa67d-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="fa67d-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="fa67d-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span><span class="sxs-lookup"><span data-stu-id="fa67d-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="fa67d-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="fa67d-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="fa67d-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="fa67d-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="fa67d-135">\<Items></span><span class="sxs-lookup"><span data-stu-id="fa67d-135">\<Items></span></span>|<span data-ttu-id="fa67d-136">\<Items></span><span class="sxs-lookup"><span data-stu-id="fa67d-136">\<Items></span></span>|<span data-ttu-id="fa67d-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-138">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-138">\<Item></span></span>|<span data-ttu-id="fa67d-139">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-139">\<Item></span></span>|<span data-ttu-id="fa67d-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-141">Test with an entity: &number;</span><span class="sxs-lookup"><span data-stu-id="fa67d-141">Test with an entity: &number;</span></span>|<span data-ttu-id="fa67d-142">Test with an entity:</span><span class="sxs-lookup"><span data-stu-id="fa67d-142">Test with an entity: 123</span></span>|<span data-ttu-id="fa67d-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fa67d-144">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-144">\</Item></span></span>|<span data-ttu-id="fa67d-145">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-145">\</Item></span></span>|<span data-ttu-id="fa67d-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fa67d-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fa67d-147">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-147">\<Item></span></span>|<span data-ttu-id="fa67d-148">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-148">\<Item></span></span>|<span data-ttu-id="fa67d-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-150">test with a child element</span><span class="sxs-lookup"><span data-stu-id="fa67d-150">test with a child element</span></span>|<span data-ttu-id="fa67d-151">test with a child element</span><span class="sxs-lookup"><span data-stu-id="fa67d-151">test with a child element</span></span>|<span data-ttu-id="fa67d-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fa67d-153">\<more></span><span class="sxs-lookup"><span data-stu-id="fa67d-153">\<more></span></span>|<span data-ttu-id="fa67d-154">\<more></span><span class="sxs-lookup"><span data-stu-id="fa67d-154">\<more></span></span>|<span data-ttu-id="fa67d-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-156">stuff</span><span class="sxs-lookup"><span data-stu-id="fa67d-156">stuff</span></span>|<span data-ttu-id="fa67d-157">stuff</span><span class="sxs-lookup"><span data-stu-id="fa67d-157">stuff</span></span>|<span data-ttu-id="fa67d-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fa67d-159">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-159">\</Item></span></span>|<span data-ttu-id="fa67d-160">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-160">\</Item></span></span>|<span data-ttu-id="fa67d-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fa67d-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fa67d-162">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-162">\<Item></span></span>|<span data-ttu-id="fa67d-163">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-163">\<Item></span></span>|<span data-ttu-id="fa67d-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-165">test with a CDATA section</span><span class="sxs-lookup"><span data-stu-id="fa67d-165">test with a CDATA section</span></span>|<span data-ttu-id="fa67d-166">test with a CDATA section</span><span class="sxs-lookup"><span data-stu-id="fa67d-166">test with a CDATA section</span></span>|<span data-ttu-id="fa67d-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="fa67d-168"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="fa67d-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="fa67d-169"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="fa67d-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="fa67d-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="fa67d-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="fa67d-171">def</span><span class="sxs-lookup"><span data-stu-id="fa67d-171">def</span></span>|<span data-ttu-id="fa67d-172">def</span><span class="sxs-lookup"><span data-stu-id="fa67d-172">def</span></span>|<span data-ttu-id="fa67d-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fa67d-174">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-174">\</Item></span></span>|<span data-ttu-id="fa67d-175">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-175">\</Item></span></span>|<span data-ttu-id="fa67d-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fa67d-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fa67d-177">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-177">\<Item></span></span>|<span data-ttu-id="fa67d-178">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-178">\<Item></span></span>|<span data-ttu-id="fa67d-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-180">Test with a char entity: &\#65;</span><span class="sxs-lookup"><span data-stu-id="fa67d-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="fa67d-181">Test with a char entity: A</span><span class="sxs-lookup"><span data-stu-id="fa67d-181">Test with a char entity: A</span></span>|<span data-ttu-id="fa67d-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fa67d-183">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-183">\</Item></span></span>|<span data-ttu-id="fa67d-184">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-184">\</Item></span></span>|<span data-ttu-id="fa67d-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fa67d-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fa67d-186">\<!-- Fourteen chars in this element.--></span><span class="sxs-lookup"><span data-stu-id="fa67d-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="fa67d-187">\<--Fourteen chars in this element.--></span><span class="sxs-lookup"><span data-stu-id="fa67d-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="fa67d-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="fa67d-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="fa67d-189">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-189">\<Item></span></span>|<span data-ttu-id="fa67d-190">\<Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-190">\<Item></span></span>|<span data-ttu-id="fa67d-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fa67d-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fa67d-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="fa67d-192">1234567890ABCD</span></span>|<span data-ttu-id="fa67d-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="fa67d-193">1234567890ABCD</span></span>|<span data-ttu-id="fa67d-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fa67d-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fa67d-195">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-195">\</Item></span></span>|<span data-ttu-id="fa67d-196">\</Item></span><span class="sxs-lookup"><span data-stu-id="fa67d-196">\</Item></span></span>|<span data-ttu-id="fa67d-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fa67d-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fa67d-198">\</Items></span><span class="sxs-lookup"><span data-stu-id="fa67d-198">\</Items></span></span>|<span data-ttu-id="fa67d-199">\</Items></span><span class="sxs-lookup"><span data-stu-id="fa67d-199">\</Items></span></span>|<span data-ttu-id="fa67d-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fa67d-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="fa67d-201">有効なアクションの種類と設定および取得できるプロパティの種類はノード型によって決まるため、割り当てられているノード型を知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa67d-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="fa67d-202">空白ノードの作成は、データが DOM に読み込まれるときに **PreserveWhitespace** フラグによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="fa67d-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="fa67d-203">詳細については、「[DOM を読み込むときの空白および有意の空白の処理](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa67d-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="fa67d-204">DOM に新しいノードを追加するには、「[XML ドキュメントへのノードの挿入](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa67d-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="fa67d-205">DOM からノードを削除するには、「[XML ドキュメントからのノード、コンテンツ、値の削除](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa67d-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="fa67d-206">DOM のノードのコンテンツを編集するには、「[XML ドキュメントのノード、コンテンツ、値の変更](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa67d-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa67d-207">参照</span><span class="sxs-lookup"><span data-stu-id="fa67d-207">See Also</span></span>  
 [<span data-ttu-id="fa67d-208">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="fa67d-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
