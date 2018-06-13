---
title: メモリ内の XML データの処理
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 317021318153cc87b2eab3db508a9dede9dc05e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569643"
---
# <a name="processing-xml-data-in-memory"></a>メモリ内の XML データの処理
Microsoft .NET Framework には、XML データを処理するためのモデルとして、<xref:System.Xml.XmlDocument> クラス、<xref:System.Xml.XPath.XPathDocument> クラス、[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) の 3 つが用意されています。  
  
 <xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) 勧告の DOM Level 1 Core および DOM Level 2 Core を実装しています。 DOM は XML ドキュメントのメモリ内 (キャッシュ) ツリー表現です。 <xref:System.Xml.XmlDocument> およびその関連クラスを使用すると、XML ドキュメントの作成、データの読み込みとアクセス、データの変更、および変更の保存が可能です。  
  
 <xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルに基づく、読み取り専用のメモリ内データ ストアです。 <xref:System.Xml.XPath.XPathNavigator> クラスは、読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスと <xref:System.Xml.XmlDocument> クラス内の XML ドキュメント全体にカーソル モデルを使用して、いくつかの編集オプションとナビゲーション機能を提供します。  
  
 [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) は、XML データの処理を目的とした Microsoft .NET Framework version 3.5 の新しいモデルです。 [LINQ (統合言語クエリ)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) を活用するメモリ内モデルです。 LINQ では C# および Visual Basic の言語構文を拡張することで、新しいクエリ機能を実現しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DOM モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <xref:System.Xml.XmlDocument> とその関連クラスを使用した XML データの処理について説明します。  
  
 [XPath データ モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument>、および <xref:System.Xml.XPath.XPathNavigator> クラスを使用した XML データの処理について説明します。  
  
 [LINQ to XML を使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 LINQ to XML の概要を簡単に説明し、LINQ to XML に関する参照先のリンクを示します。  
  
## <a name="related-sections"></a>関連項目  
 [XML ドキュメントと XML データ](../../../../docs/standard/data/xml/index.md)
