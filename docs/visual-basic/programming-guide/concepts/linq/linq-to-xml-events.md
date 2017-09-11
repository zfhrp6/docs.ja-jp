---
title: "LINQ to XML イベント (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
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
ms.openlocfilehash: e2358808dfeafab1576a686563e6025f90e78954
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="97f8c-102">LINQ to XML イベント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97f8c-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="97f8c-103">イベントを使用すると、XML ツリーが変更されるときに通知することができます。</span><span class="sxs-lookup"><span data-stu-id="97f8c-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="97f8c-104">イベントをすべて<xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>のインスタンスに追加します。</span><span class="sxs-lookup"><span data-stu-id="97f8c-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="97f8c-105">イベント ハンドラーがイベントをへの変更を受信して<xref:System.Xml.Linq.XObject>とその子孫のいずれか</xref:System.Xml.Linq.XObject>。</span><span class="sxs-lookup"><span data-stu-id="97f8c-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="97f8c-106">たとえば、イベント ハンドラーをツリーのルートに追加して、そのツリーに対するすべての変更をイベント ハンドラーから処理できます。</span><span class="sxs-lookup"><span data-stu-id="97f8c-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="97f8c-107">例については[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XObject.Changing> <xref:System.Xml.Linq.XObject.Changed>.</xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changing>イベントを参照してください</span><span class="sxs-lookup"><span data-stu-id="97f8c-107">For examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="97f8c-108">型とイベント</span><span class="sxs-lookup"><span data-stu-id="97f8c-108">Types and Events</span></span>  
 <span data-ttu-id="97f8c-109">イベントを使用する場合は、次の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="97f8c-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="97f8c-110">種類</span><span class="sxs-lookup"><span data-stu-id="97f8c-110">Type</span></span>|<span data-ttu-id="97f8c-111">説明</span><span class="sxs-lookup"><span data-stu-id="97f8c-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="97f8c-112"><xref:System.Xml.Linq.XObjectChange></xref:System.Xml.Linq.XObjectChange></span><span class="sxs-lookup"><span data-stu-id="97f8c-112"><xref:System.Xml.Linq.XObjectChange></span></span>|<span data-ttu-id="97f8c-113"><xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>イベントが発生したときに、イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="97f8c-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="97f8c-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></xref:System.Xml.Linq.XObjectChangeEventArgs></span><span class="sxs-lookup"><span data-stu-id="97f8c-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></span></span>|<span data-ttu-id="97f8c-115">データを提供、<xref:System.Xml.Linq.XObject.Changing>と<xref:System.Xml.Linq.XObject.Changed>イベント</xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changing>。</span><span class="sxs-lookup"><span data-stu-id="97f8c-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="97f8c-116">XML ツリーを変更するときに次のイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="97f8c-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="97f8c-117">Event</span><span class="sxs-lookup"><span data-stu-id="97f8c-117">Event</span></span>|<span data-ttu-id="97f8c-118">説明</span><span class="sxs-lookup"><span data-stu-id="97f8c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97f8c-119"><xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="97f8c-119"><xref:System.Xml.Linq.XObject.Changing></span></span>|<span data-ttu-id="97f8c-120">この直前に発生<xref:System.Xml.Linq.XObject>を変更またはその子孫のいずれかができます</xref:System.Xml.Linq.XObject>。</span><span class="sxs-lookup"><span data-stu-id="97f8c-120">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<span data-ttu-id="97f8c-121"><xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changed></span><span class="sxs-lookup"><span data-stu-id="97f8c-121"><xref:System.Xml.Linq.XObject.Changed></span></span>|<span data-ttu-id="97f8c-122">発生したときに、<xref:System.Xml.Linq.XObject>が変更またはその子孫のいずれかの変更されています</xref:System.Xml.Linq.XObject>。</span><span class="sxs-lookup"><span data-stu-id="97f8c-122">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97f8c-123">例</span><span class="sxs-lookup"><span data-stu-id="97f8c-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="97f8c-124">説明</span><span class="sxs-lookup"><span data-stu-id="97f8c-124">Description</span></span>  
 <span data-ttu-id="97f8c-125">XML ツリー内の集計情報を維持する場合に、イベントは便利です。</span><span class="sxs-lookup"><span data-stu-id="97f8c-125">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="97f8c-126">たとえば、請求書の品目の合計である請求合計を維持する場合があります。</span><span class="sxs-lookup"><span data-stu-id="97f8c-126">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="97f8c-127">この例では、イベントを使用して、複合要素の `Items` の下にあるすべての子要素の合計を維持します。</span><span class="sxs-lookup"><span data-stu-id="97f8c-127">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="97f8c-128">コード</span><span class="sxs-lookup"><span data-stu-id="97f8c-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="97f8c-129">コメント</span><span class="sxs-lookup"><span data-stu-id="97f8c-129">Comments</span></span>  
 <span data-ttu-id="97f8c-130">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97f8c-130">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97f8c-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="97f8c-131">See Also</span></span>  
 [<span data-ttu-id="97f8c-132">高度な LINQ to XML のプログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97f8c-132">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
