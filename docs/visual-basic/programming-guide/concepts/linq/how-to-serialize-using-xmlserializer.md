---
title: "方法: XmlSerializer (Visual Basic) を使用してシリアル化"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cace24eb-0f43-4016-8e4b-199e5ef73a1c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d137296f6f4006cd222ebfa5e36e04d41f6ab9f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-serialize-using-xmlserializer-visual-basic"></a><span data-ttu-id="5b136-102">方法: XmlSerializer (Visual Basic) を使用してシリアル化</span><span class="sxs-lookup"><span data-stu-id="5b136-102">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>
<span data-ttu-id="5b136-103">このトピックでは、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化および逆シリアル化を行う例について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b136-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b136-104">例</span><span class="sxs-lookup"><span data-stu-id="5b136-104">Example</span></span>  
 <span data-ttu-id="5b136-105">次の例では、<xref:System.Xml.Linq.XElement> オブジェクトを含んでいる多数のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b136-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="5b136-106">次に、それらのオブジェクトをメモリ ストリームにシリアル化し、メモリ ストリームから逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="5b136-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
Imports System.Xml.Serialization  
  
Public Class XElementContainer  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
  
    Overrides Function ToString() As String  
        Return member.ToString()  
    End Function  
End Class  
  
Public Class XElementNullContainer  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Dim ns As XNamespace = "http://www.adventure-works.com"  
        Return New XElement(ns + "aw")  
    End Function  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Using stream As New MemoryStream()  
            Dim s As XmlSerializer = New XmlSerializer(GetType(T))  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.Serialize(XmlWriter.Create(stream), obj)  
            stream.Flush()  
            stream.Seek(0, SeekOrigin.Begin)  
            Dim o As Object = s.Deserialize(XmlReader.Create(stream))  
            Console.WriteLine("  Deserialized type: {0}", o.GetType())  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5b136-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5b136-107">This example produces the following output:</span></span>  
  
```  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b136-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b136-108">See Also</span></span>  
 [<span data-ttu-id="5b136-109">XElement オブジェクト (Visual Basic) を格納するオブジェクト グラフをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="5b136-109">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
