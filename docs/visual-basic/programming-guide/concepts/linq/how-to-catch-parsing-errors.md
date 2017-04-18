---
title: "方法: 解析エラー (Visual Basic) をキャッチ |Microsoft ドキュメント"
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
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0c4ba619d1f269352b3288f6cadf3b6f37a0dc2d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>方法: 解析エラー (Visual Basic) をキャッチ
このトピックでは、形式が正しくないか無効な XML を検出する方法について説明します。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>を使用して実装されます。 形式が正しくないか、無効な XML が渡された場合[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]、基になる<xref:System.Xml.XmlReader>クラスは例外をスローします</xref:System.Xml.XmlReader>。 さまざまな方法など、XML を解析する<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、例外をキャッチしませんアプリケーションで例外をキャッチし、ことができます。</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName> 。  
  
 XML リテラルを使用する場合は、解析エラーを検出できないことに注意してください。 Visual Basic コンパイラは、形式が正しくないか無効な XML をキャッチします。  
  
## <a name="example"></a>例  
 次のコードでは、無効な XML の解析を試行します。  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 このコードを実行すると、次の例外がスローされます。  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 予期される例外について、 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>、 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、および<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>をスローするメソッドを参照してください、<xref:System.Xml.XmlReader>ドキュメント</xref:System.Xml.XmlReader></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>。  
  
## <a name="see-also"></a>関連項目  
 [(Visual Basic) の XML の解析](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
