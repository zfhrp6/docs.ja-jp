---
title: "方法: 解析エラーをキャッチする (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf9469a328d80cca95fc5da2b143a494490089c2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-parsing-errors-c"></a>方法: 解析エラーをキャッチする (C#)
このトピックでは、形式が正しくないか無効な XML を検出する方法について説明します。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] は、<xref:System.Xml.XmlReader> を使用して実装されています。 形式が正しくない XML や無効な XML が [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] に渡されると、基になる <xref:System.Xml.XmlReader> クラスから例外がスローされます。 XML を解析するさまざまなメソッド (<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName> など) はこの例外をキャッチしません。この例外は、アプリケーションでキャッチできます。  
  
## <a name="example"></a>例  
 次のコードでは、無効な XML の解析を試行します。  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 このコードを実行すると、次の例外がスローされます。  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> の各メソッドからスローされる可能性のある例外については、<xref:System.Xml.XmlReader> のドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [XML の解析 (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
