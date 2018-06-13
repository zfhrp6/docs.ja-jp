---
title: '方法: DataContractSerializer を使用してシリアル化する (C#)'
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 1b2ec431698f23ea0c3e690cd57261bad8b1e4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329285"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="9184d-102">方法: DataContractSerializer を使用してシリアル化する (C#)</span><span class="sxs-lookup"><span data-stu-id="9184d-102">How to: Serialize Using DataContractSerializer (C#)</span></span>
<span data-ttu-id="9184d-103">このトピックでは、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化および逆シリアル化を行う例について説明します。</span><span class="sxs-lookup"><span data-stu-id="9184d-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9184d-104">例</span><span class="sxs-lookup"><span data-stu-id="9184d-104">Example</span></span>  
 <span data-ttu-id="9184d-105">次の例では、<xref:System.Xml.Linq.XElement> オブジェクトを含んでいる多数のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9184d-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="9184d-106">次に、それらのオブジェクトをテキスト ファイルにシリアル化し、テキスト ファイルから逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="9184d-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));   
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="9184d-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9184d-107">This example produces the following output:</span></span>  
  
```  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="9184d-108">参照</span><span class="sxs-lookup"><span data-stu-id="9184d-108">See Also</span></span>  
 [<span data-ttu-id="9184d-109">XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="9184d-109">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
