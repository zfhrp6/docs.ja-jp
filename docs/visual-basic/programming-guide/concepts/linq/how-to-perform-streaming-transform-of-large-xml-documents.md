---
title: "方法: 大きな XML ドキュメント (Visual Basic) のストリーミング変換を実行 |Microsoft ドキュメント"
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
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 730039a85c8c72b9379617cb4b3c019028c3a1e9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="fc209-102">方法: 大きな XML ドキュメント (Visual Basic) のストリーミング変換を実行</span><span class="sxs-lookup"><span data-stu-id="fc209-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="fc209-103">大きな XML ファイルを変換して、アプリケーションのメモリ使用量を予想できるようにアプリケーションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc209-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="fc209-104">非常に大きな XML ファイルを XML ツリーに設定しようとすると、ファイルのサイズに比例してメモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc209-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="fc209-105">したがって、代わりにストリーミングの手法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc209-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="fc209-106">ストリーミングの手法は、ソース ドキュメントを&1; 回だけ処理する必要がある場合に適しており、ドキュメントの順序で要素を処理できます。</span><span class="sxs-lookup"><span data-stu-id="fc209-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="fc209-107">一部の標準クエリ演算子でなど<xref:System.Linq.Enumerable.OrderBy%2A>、そのソースを反復処理する、すべてのデータを収集、並べ替えられて、および最終的に、シーケンスの最初の項目が生成されます</xref:System.Linq.Enumerable.OrderBy%2A>。</span><span class="sxs-lookup"><span data-stu-id="fc209-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="fc209-108">最初の項目を生成する前にソースを具体化するクエリ演算子を使用すると、アプリケーションのメモリ使用量を低く維持することができないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="fc209-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="fc209-109">説明したテクニックを使用する場合でも[方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)、変換されたドキュメントのメモリ使用量が非常に高いを含む XML ツリーをアセンブルしようとする場合。</span><span class="sxs-lookup"><span data-stu-id="fc209-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="fc209-110">主な方法は&2; つあります。</span><span class="sxs-lookup"><span data-stu-id="fc209-110">There are two main approaches.</span></span> <span data-ttu-id="fc209-111">1 つの方法は、 <xref:System.Xml.Linq.XStreamingElement>。</xref:System.Xml.Linq.XStreamingElement>の遅延処理の特性を使用するには</span><span class="sxs-lookup"><span data-stu-id="fc209-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="fc209-112">別の方法は、作成する、<xref:System.Xml.XmlWriter>の機能を使用して[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>に要素を書き込む</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="fc209-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="fc209-113">このトピックでは、両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc209-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc209-114">例</span><span class="sxs-lookup"><span data-stu-id="fc209-114">Example</span></span>  
 <span data-ttu-id="fc209-115">次の例では、例では、ビルド[方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)します。</span><span class="sxs-lookup"><span data-stu-id="fc209-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="fc209-116">この例の遅延実行機能を使用して<xref:System.Xml.Linq.XStreamingElement>してストリーム出力します</xref:System.Xml.Linq.XStreamingElement>。</span><span class="sxs-lookup"><span data-stu-id="fc209-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="fc209-117">この例を使用すると、メモリ使用量を低く抑えながら、非常に大きなドキュメントを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="fc209-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="fc209-118">カスタム軸 (`StreamCustomerItem`) は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、次に示す Source.xml ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="fc209-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="fc209-119">ただし、より堅牢に実装する場合は、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="fc209-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="fc209-120">ソース ドキュメント Source.xml を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fc209-120">The following is the source document, Source.xml:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root = New XStreamingElement("Root",  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
            )  
        root.Save("Test.xml")  
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))  
    End Sub  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="fc209-121">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc209-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="fc209-122">例</span><span class="sxs-lookup"><span data-stu-id="fc209-122">Example</span></span>  
 <span data-ttu-id="fc209-123">次の例は、の例でもビルド[方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)します。</span><span class="sxs-lookup"><span data-stu-id="fc209-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="fc209-124">この例の機能を使用して[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>に要素を書き込む</span><span class="sxs-lookup"><span data-stu-id="fc209-124">This example uses the capability of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="fc209-125">この例を使用すると、メモリ使用量を低く抑えながら、非常に大きなドキュメントを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="fc209-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="fc209-126">カスタム軸 (`StreamCustomerItem`) は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、次に示す Source.xml ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="fc209-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="fc209-127">ただし、より堅牢に実装する場合は、ソース ドキュメントを XSD で検証するか、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="fc209-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="fc209-128">この例でも、このトピックの前の例と同じソース ドキュメント Source.xml を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc209-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="fc209-129">生成される出力も同じになります。</span><span class="sxs-lookup"><span data-stu-id="fc209-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="fc209-130"><xref:System.Xml.Linq.XStreamingElement>XML は<xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>を記述するより優先される出力のストリーミングに</xref:System.Xml.Linq.XStreamingElement>使用します。</span><span class="sxs-lookup"><span data-stu-id="fc209-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim srcTree =  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
  
        Dim xws = New Xml.XmlWriterSettings()  
        xws.OmitXmlDeclaration = True  
        xws.Indent = True  
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)  
            xw.WriteStartElement("Root")  
            For Each el In srcTree  
                el.WriteTo(xw)  
            Next  
            xw.WriteEndElement()  
        End Using  
  
        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")  
        Console.WriteLine(s)  
    End Sub  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="fc209-131">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc209-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc209-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc209-132">See Also</span></span>  
 [<span data-ttu-id="fc209-133">高度な LINQ to XML のプログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc209-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
