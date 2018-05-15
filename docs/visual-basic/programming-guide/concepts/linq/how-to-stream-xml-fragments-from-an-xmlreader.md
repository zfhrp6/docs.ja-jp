---
title: '方法: XML フラグメントをストリームから XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 38a81e83421dffc997a2cbfd6d0996da5ece18d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="cae5c-102">方法: XML フラグメントをストリームから XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cae5c-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="cae5c-103">大きな XML ファイルを処理する必要があるときに、XML ツリー全体をメモリに読み込むことができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="cae5c-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="cae5c-104">このトピックでは、<xref:System.Xml.XmlReader> を使用してフラグメントをストリーム出力する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cae5c-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="cae5c-105"><xref:System.Xml.XmlReader> を使用して <xref:System.Xml.Linq.XElement> オブジェクトを読み取るための最も効果的な方法の 1 つは、カスタムの軸メソッドを独自に記述することです。</span><span class="sxs-lookup"><span data-stu-id="cae5c-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="cae5c-106">一般に軸メソッドは、このトピックの例で示すように、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> などのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="cae5c-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="cae5c-107">カスタムの軸メソッドでは、<xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドを呼び出して XML フラグメントを作成した後に、`yield return` を使用してコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="cae5c-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="cae5c-108">これにより、カスタムの軸メソッドに遅延実行セマンティクスが付加されます。</span><span class="sxs-lookup"><span data-stu-id="cae5c-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="cae5c-109"><xref:System.Xml.XmlReader> オブジェクトから XML ツリーを作成する場合は、<xref:System.Xml.XmlReader> を要素に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cae5c-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="cae5c-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドは、要素の終了タグを読み取るまで制御を戻しません。</span><span class="sxs-lookup"><span data-stu-id="cae5c-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="cae5c-111">部分ツリーを作成する場合は、<xref:System.Xml.XmlReader> をインスタンス化し、<xref:System.Xml.Linq.XElement> ツリーに変換するノード上にリーダーを配置し、<xref:System.Xml.Linq.XElement> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cae5c-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="cae5c-112">トピック[する方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)情報より複雑なドキュメントをストリーミングする方法の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cae5c-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="cae5c-113">トピック[する方法: 実行のストリーミング変換の大きな XML ドキュメント (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)小規模メモリ フット プリントを維持しながら、非常に大きな XML ドキュメントを変換する LINQ to XML の使用例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cae5c-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae5c-114">例</span><span class="sxs-lookup"><span data-stu-id="cae5c-114">Example</span></span>  
 <span data-ttu-id="cae5c-115">次の例では、カスタムの軸メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="cae5c-115">This example creates a custom axis method.</span></span> <span data-ttu-id="cae5c-116">このメソッドに対してクエリを実行するには、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="cae5c-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="cae5c-117">カスタムの軸メソッド `StreamRootChildDoc` は、`Child` 要素が繰り返し出現するドキュメントを読み取るために特に設計されたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="cae5c-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
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
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
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
  
 <span data-ttu-id="cae5c-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cae5c-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="cae5c-119">この例のソース ドキュメントは、非常に小さなドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="cae5c-119">In this example, the source document is very small.</span></span> <span data-ttu-id="cae5c-120">ただし、何百万の `Child` 要素があっても、この例で使用されるメモリは非常に少量です。</span><span class="sxs-lookup"><span data-stu-id="cae5c-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae5c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="cae5c-121">See Also</span></span>  
 [<span data-ttu-id="cae5c-122">チュートリアル: Visual Basic での IEnumerable(Of T) の実装</span><span class="sxs-lookup"><span data-stu-id="cae5c-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [<span data-ttu-id="cae5c-123">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="cae5c-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
