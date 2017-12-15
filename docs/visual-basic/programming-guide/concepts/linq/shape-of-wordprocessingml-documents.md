---
title: "WordprocessingML ドキュメント (Visual Basic) の構造"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5809e8148e7ac426b876ad11948878ee0bfcd016
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>WordprocessingML ドキュメント (Visual Basic) の構造
このトピックでは、WordprocessingML ドキュメントの XML 構造について説明します。  
  
## <a name="microsoft-office-formats"></a>Microsoft Office 形式  
 2007 Microsoft Office システムのネイティブ ファイル形式は Office Open XML (一般的な呼称は Open XML) です。 Open XML は Ecma 標準の XML ベースの形式であり、現在は ISO-IEC 標準としての検討が進められている段階です。 Open XML 内のワード プロセッシング ファイルのマークアップ言語は WordprocessingML と呼ばれます。 このチュートリアルの例では、WordprocessingML ソース ファイルを入力として使用します。  
  
 Microsoft Office 2003 を使用している場合は、Word、Excel、PowerPoint 2007 File Formats を Microsoft Office 互換機能パックをインストールした場合、Office Open XML 形式でドキュメントを保存できます。  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>WordprocessingML ドキュメントの構造  
 最初に理解する必要があるのは WordprocessingML ドキュメントの構造です。 WordprocessingML ドキュメントには、ドキュメントの段落を含む本文要素 (名前は `w:body`) が 1 つあります。 各段落には、1 つ以上のテキスト ラン (名前は `w:r`) が含まれています。 各テキスト ランには、1 つ以上のテキスト片 (名前は `w:t`) が含まれています。  
  
 非常に単純な WordprocessingML ドキュメントを次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 このドキュメントには、2 つの段落が含まれています。 各段落には 1 つのテキスト ランが含まれており、各テキスト ランには 1 つのテキスト片が含まれています。  
  
 WordprocessingML ドキュメントの内容を XML 形式で表示する最も簡単な方法は、Microsoft Word を使用して WordprocessingML ドキュメントを作成および保存し、次のプログラムを実行してコンソールに XML を出力することです。  
  
 この例では、WindowsBase アセンブリに含まれるクラスを使用します。 また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a>外部リソース  
 [Office (2007) Open XML ファイル形式の概要](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [WordprocessingML の概要](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [Office 2003: XML リファレンス スキーマのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
