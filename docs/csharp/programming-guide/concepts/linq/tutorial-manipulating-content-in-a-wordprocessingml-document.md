---
title: "チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dca728cf48c6af6437beb43bcb6a8c8b7283d639
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2018
---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a>チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)
このチュートリアルでは、関数型変換の方法と LINQ to XML を適用して XML ドキュメントを操作する方法について説明します。 C# の例では、Microsoft Word で保存された Office Open XML WordprocessingML ドキュメント内の情報をクエリして操作します。  
  
 詳細については、[WordprocessingML の概要](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)に関するページを参照してください。  
  
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
  
## <a name="see-also"></a>参照  
 [XML の純粋関数型変換 (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)  
 [純粋関数型変換の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
