---
title: "LINQ to XML イベント (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19d8f19f9feb1d385f9900d76d2a7af8e89bbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="2fd59-102">LINQ to XML イベント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fd59-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2fd59-103"> イベントを使うと、XML ツリーが変更されるときに通知を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="2fd59-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="2fd59-104">イベントは、任意の <xref:System.Xml.Linq.XObject> のインスタンスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2fd59-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="2fd59-105">イベント ハンドラーは、その <xref:System.Xml.Linq.XObject> およびその任意の子孫に対する変更のイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2fd59-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="2fd59-106">たとえば、イベント ハンドラーをツリーのルートに追加して、そのツリーに対するすべての変更をイベント ハンドラーから処理できます。</span><span class="sxs-lookup"><span data-stu-id="2fd59-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="2fd59-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] イベントの例については、<xref:System.Xml.Linq.XObject.Changing> および <xref:System.Xml.Linq.XObject.Changed> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fd59-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="2fd59-108">型とイベント</span><span class="sxs-lookup"><span data-stu-id="2fd59-108">Types and Events</span></span>  
 <span data-ttu-id="2fd59-109">イベントを使用する場合は、次の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2fd59-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="2fd59-110">種類</span><span class="sxs-lookup"><span data-stu-id="2fd59-110">Type</span></span>|<span data-ttu-id="2fd59-111">説明</span><span class="sxs-lookup"><span data-stu-id="2fd59-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="2fd59-112"><xref:System.Xml.Linq.XObject> に対してイベントが生成されるときのイベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fd59-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="2fd59-113"><xref:System.Xml.Linq.XObject.Changing> イベントおよび <xref:System.Xml.Linq.XObject.Changed> イベントのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="2fd59-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="2fd59-114">XML ツリーを変更するときに次のイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="2fd59-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="2fd59-115">Event</span><span class="sxs-lookup"><span data-stu-id="2fd59-115">Event</span></span>|<span data-ttu-id="2fd59-116">説明</span><span class="sxs-lookup"><span data-stu-id="2fd59-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="2fd59-117"><xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更される直前に発生します。</span><span class="sxs-lookup"><span data-stu-id="2fd59-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="2fd59-118"><xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2fd59-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2fd59-119">例</span><span class="sxs-lookup"><span data-stu-id="2fd59-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2fd59-120">説明</span><span class="sxs-lookup"><span data-stu-id="2fd59-120">Description</span></span>  
 <span data-ttu-id="2fd59-121">XML ツリー内の集計情報を維持する場合に、イベントは便利です。</span><span class="sxs-lookup"><span data-stu-id="2fd59-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="2fd59-122">たとえば、請求書の品目の合計である請求合計を維持する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2fd59-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="2fd59-123">この例では、イベントを使用して、複合要素の `Items` の下にあるすべての子要素の合計を維持します。</span><span class="sxs-lookup"><span data-stu-id="2fd59-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2fd59-124">コード</span><span class="sxs-lookup"><span data-stu-id="2fd59-124">Code</span></span>  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="2fd59-125">コメント</span><span class="sxs-lookup"><span data-stu-id="2fd59-125">Comments</span></span>  
 <span data-ttu-id="2fd59-126">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2fd59-126">This code produces the following output:</span></span>  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fd59-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fd59-127">See Also</span></span>  
 [<span data-ttu-id="2fd59-128">高度な LINQ to XML プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fd59-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
