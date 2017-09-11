---
title: "方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム出力 |Microsoft ドキュメント"
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
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 2ec1d189daa5460d3b90ea8609ea74eefcd70b7f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="d9906-102">方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム出力</span><span class="sxs-lookup"><span data-stu-id="d9906-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="d9906-103">大きな XML ファイルを任意に読み取り、アプリケーションのメモリ使用量を予想できるようにアプリケーションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9906-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="d9906-104">大きな XML ファイルを XML ツリーに設定しようとすると、ファイルのサイズに比例してメモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d9906-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="d9906-105">したがって、代わりにストリーミングの手法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9906-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="d9906-106">1 つのオプションが<xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>を使用してアプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="d9906-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d9906-107">ただし、使用する場合があります[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]XML ツリーに対してクエリします。</span><span class="sxs-lookup"><span data-stu-id="d9906-107">However, you might want to use [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to query the XML tree.</span></span> <span data-ttu-id="d9906-108">このような場合は、カスタムの軸メソッドを独自に記述します。</span><span class="sxs-lookup"><span data-stu-id="d9906-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="d9906-109">詳細については、次を参照してください。[方法:、LINQ to XML 軸メソッド (Visual Basic) を記述](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)します。</span><span class="sxs-lookup"><span data-stu-id="d9906-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="d9906-110">使用する小さなメソッドを記述する、独自の軸メソッドを記述する、<xref:System.Xml.XmlReader>対象のノードのいずれかに達するまで、ノードを読み取れません</xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="d9906-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="d9906-111">メソッドを呼び出して、<xref:System.Xml.Linq.XNode.ReadFrom%2A>からを読み取ります、<xref:System.Xml.XmlReader>し、XML フラグメントをインスタンス化します</xref:System.Xml.XmlReader></xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="d9906-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="d9906-112">これで、カスタムの軸メソッド上に LINQ クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="d9906-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="d9906-113">ストリーミングの手法は、ソース ドキュメントを&1; 回だけ処理する必要がある場合に適しており、ドキュメントの順序で要素を処理できます。</span><span class="sxs-lookup"><span data-stu-id="d9906-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="d9906-114">一部の標準クエリ演算子でなど<xref:System.Linq.Enumerable.OrderBy%2A>、そのソースを反復処理する、すべてのデータを収集、並べ替えられて、および最終的に、シーケンスの最初の項目が生成されます</xref:System.Linq.Enumerable.OrderBy%2A>。</span><span class="sxs-lookup"><span data-stu-id="d9906-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="d9906-115">最初の項目を生成する前にソースを具体化するクエリ演算子を使用すると、メモリ使用量を低く維持することができないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="d9906-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9906-116">例</span><span class="sxs-lookup"><span data-stu-id="d9906-116">Example</span></span>  
 <span data-ttu-id="d9906-117">ストリーム出力は関心の高い問題となる場合があるため、例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="d9906-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="d9906-118">次の XML ドキュメントでは、カスタムの軸メソッドのコンシューマーが、各項目が属している顧客の名前も認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9906-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="d9906-119">この例で採用している方法では、ヘッダー情報の監視と保存が行われ、その後でヘッダー情報と列挙される詳細情報の両方が含まれている小さな XML ツリーが構築されます。</span><span class="sxs-lookup"><span data-stu-id="d9906-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="d9906-120">次に、軸メソッドによってこの新しい小さな XML ツリーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d9906-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="d9906-121">これでクエリは、詳細情報だけでなくヘッダー情報にもアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d9906-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="d9906-122">この方法で使用されるメモリは少量です。</span><span class="sxs-lookup"><span data-stu-id="d9906-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="d9906-123">詳細な XML フラグメントが個々に生成されるときに、前のフラグメントへの参照は保持されず、そのフラグメントはガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="d9906-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="d9906-124">この手法を使用すると、存続期間の短いオブジェクトがヒープ上に多数作成されるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="d9906-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="d9906-125">次の例では、URI で指定されたファイルから XML フラグメントをストリーム出力する、カスタムの軸メソッドを実装して使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d9906-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="d9906-126">このカスタムの軸は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、上記の `Source.xml` ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="d9906-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="d9906-127">これは単純な実装です。</span><span class="sxs-lookup"><span data-stu-id="d9906-127">It is a simplistic implementation.</span></span> <span data-ttu-id="d9906-128">ただし、より堅牢に実装する場合は、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="d9906-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim xmlTree = <Root>  
                          <%=  
                              From el In New StreamCustomerItem("Source.xml")  
                              Let itemKey = CInt(el.<Key>.Value)  
                              Where itemKey >= 3 AndAlso itemKey <= 7  
                              Select <Item>  
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>  
                                         <%= el.<Key> %>  
                                     </Item>  
                          %>  
                      </Root>  
  
        Console.WriteLine(xmlTree)  
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
  
 <span data-ttu-id="d9906-129">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d9906-129">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9906-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9906-130">See Also</span></span>  
 [<span data-ttu-id="d9906-131">高度な LINQ to XML のプログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9906-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

