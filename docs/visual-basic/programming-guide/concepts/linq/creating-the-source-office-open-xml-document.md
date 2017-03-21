---
title: "ソース Office Open XML ドキュメント (Visual Basic) を作成する |Microsoft ドキュメント"
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
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 928a3c34836464e7603c485b64c9c426913ae7b2
ms.lasthandoff: 03/13/2017


---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>ソース Office Open XML ドキュメント (Visual Basic) を作成します。
このトピックでは、このチュートリアルの他の例で使用する Office Open XML WordprocessingML ドキュメントを作成する方法について説明します。 この手順に従うと、それぞれの例に記載されているとおりの出力が得られます。  
  
 ただし、このチュートリアルの例では、任意の有効な WordprocessingML ドキュメントを使用できます。  
  
 このチュートリアルで使用するドキュメントを作成するには、Microsoft Office 2007 が必要か、または以降がインストールされて、または Microsoft Office 2003 と Microsoft Office Compatibility Pack for Word、Excel、および PowerPoint 2007 File Formats する必要があります。  
  
## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML ドキュメントの作成  
  
#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML ドキュメントを作成するには  
  
1.  新しい Microsoft Word 文書を作成します。  
  
2.  新しい文書に次のテキストを貼り付けます。  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  "見出し 1" スタイルを使用して最初の行を書式設定します。  
  
4.  Visual Basic コードを含む行を選択します。 最初の行は `Imports` キーワードで始まります。 最後の行は、"End Class"です。 クーリエ フォントを使用してこれらの行を書式設定します。 これらの行を新しいスタイルで書式設定し、このスタイルに "Code" という名前を付けます。  
  
5.  最後に、出力が含まれる行全体を選択し、`Code` スタイルを使用して書式設定します。  
  
6.  ドキュメントを保存し、SampleDoc.docx という名前を付けます。  
  
    > [!NOTE]
    >  Microsoft Word 2003 を使用している場合は、選択**Word 2007 文書**で、**ファイルの種類**ボックスの一覧です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
