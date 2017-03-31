---
title: "チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#) | Microsoft Docs"
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
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e36db410781765c6861f60942782bbd6259d5de8
ms.lasthandoff: 03/13/2017


---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a>チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)
このチュートリアルでは、関数型変換の方法と LINQ to XML を適用して XML ドキュメントを操作する方法について説明します。 C# の例では、Microsoft Word で保存された Office Open XML WordprocessingML ドキュメント内の情報をクエリして操作します。  
  
 詳細については、[OpenXML 開発者](http://go.microsoft.com/fwlink/?LinkID=95573)の Web サイトを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[WordprocessingML ドキュメントの構造 (C#)](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|WordprocessingML ドキュメントの詳細について簡単に説明します。|  
|[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|このチュートリアルのクエリのソース ドキュメントを作成するための手順について説明します。|  
|[既定の段落スタイルの検索 (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|ドキュメントの既定のスタイルの名前を検索するクエリについて説明します。|  
|[段落とそのスタイルの取得 (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|ドキュメントの段落のコレクションを取得するクエリについて説明します。|  
|[段落のテキストの取得 (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|前のクエリを拡張して各段落のテキストを取得します。|  
|[拡張メソッドを使用したリファクタリング (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|拡張メソッドを使用してリファクタリングすることにより、コードを簡略化します。|  
|[純粋関数によるリファクタリング (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|純粋関数を使用してリファクタリングすることにより、コードをさらに簡略化します。|  
|[異なる構造の XML の射影 (C#)](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|元のドキュメントとは異なる構造の XML を射影することにより、XML 変換を完了します。|  
|[Word 文書内のテキストの検索 (C#)](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|前のクエリを使用してドキュメント内の指定された文字列を検索します。|  
|[Office Open XML WordprocessingML ドキュメントの詳細 (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|Office Open XML WordprocessingML ドキュメントの詳細について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [XML の純粋関数型変換 (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)   
 [純粋関数型変換の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
