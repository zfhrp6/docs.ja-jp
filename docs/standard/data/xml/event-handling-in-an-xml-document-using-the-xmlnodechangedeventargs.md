---
title: "XmlNodeChangedEventArgs による XML ドキュメントのイベント処理"
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
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2bfd6eee5831b6bb92c0274fe5925184c80a92e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a>XmlNodeChangedEventArgs による XML ドキュメントのイベント処理
**XmlNodeChangedEventArgs**に登録されたイベント ハンドラーに渡される引数をカプセル化、 **XmlDocument**イベントを処理するオブジェクト。 各イベントとその発生するタイミングを次の表に示します。  
  
|Event|発生するタイミング|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|現在のドキュメントに属するノードが別のノードに挿入されるとき。|  
|<xref:System.Xml.XmlDocument.NodeInserted>|現在のドキュメントに属するノードが別のノードに挿入されたとき。|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|このドキュメントに属するノードがドキュメントから削除されるとき。|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|このドキュメントに属するノードがその親から削除されたとき。|  
|<xref:System.Xml.XmlDocument.NodeChanging>|ノードの値が変更されるとき。|  
|<xref:System.Xml.XmlDocument.NodeChanged>|ノードの値が変更されたとき。|  
  
> [!NOTE]
>  場合、 **XmlDataDocument**を使用する最適化が完全にメモリ使用量**データセット**、ストレージ、 **XmlDataDocument**の変更時に、上記のイベントを発生させません可能性があります基になるに加えられた**データセット**です。 これらのイベントを必要がある場合は、全体を走査する必要があります**XmlDocument**最適化が完全でないメモリ使用量を 1 回です。  
  
 イベント ハンドラーを定義する方法、およびイベント ハンドラーをイベントに追加する方法を次のコード サンプルに示します。  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)   
AddHandler doc.NodeInserted, XmlNodeChgEHdlr   
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )   
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )   
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );   
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 XML ドキュメント オブジェクト モデル (DOM) の操作の中には、複数のイベントが発生する複合操作があります。 たとえば、 **AppendChild**以前の親から追加するノードを削除することもできます。 この場合、表示、 **NodeRemoved**最初に、発生したイベントが続く、 **NodeInserted**イベント。 設定する操作など**InnerXml**複数のイベントが発生する可能性があります。  
  
 イベント ハンドラーの作成との処理は、次のコード例を示しています、 **NodeInserted**イベント。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);             
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class   
```  
  
 詳細については、<xref:System.Xml.XmlNodeChangedEventArgs> および <xref:System.Xml.XmlNodeChangedEventHandler> を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
