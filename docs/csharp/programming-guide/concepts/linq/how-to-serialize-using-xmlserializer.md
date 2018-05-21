---
title: '方法: XmlSerializer を使用してシリアル化する (C#)'
ms.date: 07/20/2015
ms.assetid: 2e0a0bbc-c548-4fe2-8741-be5a9ccd0cbb
ms.openlocfilehash: 2f68253f2ce1efaaabb971350496898ab012706b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-serialize-using-xmlserializer-c"></a><span data-ttu-id="8e8be-102">方法: XmlSerializer を使用してシリアル化する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e8be-102">How to: Serialize Using XmlSerializer (C#)</span></span>
<span data-ttu-id="8e8be-103">このトピックでは、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化および逆シリアル化を行う例について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e8be-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e8be-104">例</span><span class="sxs-lookup"><span data-stu-id="8e8be-104">Example</span></span>  
 <span data-ttu-id="8e8be-105">次の例では、<xref:System.Xml.Linq.XElement> オブジェクトを含んでいる多数のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e8be-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8e8be-106">次に、それらのオブジェクトをメモリ ストリームにシリアル化し、メモリ ストリームから逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="8e8be-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Linq;  
using System.Xml;  
using System.Xml.Serialization;  
using System.Xml.Linq;  
  
public class XElementContainer  
{  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
  
    public override string ToString()  
    {  
        return member.ToString();  
    }  
}  
  
public class XElementNullContainer  
{  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
    }  
}  
  
class XLinqTest  
{  
    static void Main(string[] args)  
    {  
        Test<XElementNullContainer>(new XElementNullContainer());  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
    }  
  
    public static XElement CreateXElement()  
    {  
        XNamespace ns = "http://www.adventure-works.com";  
        return new XElement(ns + "aw");  
    }  
  
    static void Test<T>(T obj)  
    {  
        using (MemoryStream stream = new MemoryStream())  
        {  
            XmlSerializer s = new XmlSerializer(typeof(T));  
            Console.WriteLine("Testing for type: {0}", typeof(T));  
            s.Serialize(XmlWriter.Create(stream), obj);  
            stream.Flush();  
            stream.Seek(0, SeekOrigin.Begin);  
            object o = s.Deserialize(XmlReader.Create(stream));  
            Console.WriteLine("  Deserialized type: {0}", o.GetType());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8e8be-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8e8be-107">This example produces the following output:</span></span>  
  
```  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e8be-108">参照</span><span class="sxs-lookup"><span data-stu-id="8e8be-108">See Also</span></span>  
 [<span data-ttu-id="8e8be-109">XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="8e8be-109">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
