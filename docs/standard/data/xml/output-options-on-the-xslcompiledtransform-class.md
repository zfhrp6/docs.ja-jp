---
title: "XslCompiledTransform クラスの出力オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XslCompiledTransform クラスの出力オプション
このトピックでは、XSLT で使用できる出力オプションについて説明します。  出力オプションは、スタイル シート内で、または <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドで指定できます。  
  
## xsl:output 要素  
 `xsl:output` 要素は出力のオプションを指定します。  <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドで指定する出力の種類により、`xsl:output` オプションの動作が決定されます。  
  
 次の表では、出力の種類がストリームか <xref:System.IO.TextWriter> の場合に `xsl:output` 要素で使用できる各属性の動作について説明します。  
  
|属性名|動作|  
|---------|--------|  
|メソッド|サポートされています。|  
|version|無視されます。  バージョンは常に XML では 1.0、そして HTML では 4.0 です。|  
|encoding|<xref:System.IO.TextWriter> への出力時には無視されます。  <xref:System.IO.TextWriter.Encoding%2A?displayProperty=fullName> プロパティが代わりに使用されます。|  
|omit\-xml\-declaration|サポートされています。|  
|スタンドアロン|サポートされています。|  
|doctype\-public|サポートされています。|  
|doctype\-system|サポートされています。|  
|cdata\-section\-elements|サポートされています。|  
|indent|サポートされています。|  
|media\-type|サポートされています。|  
  
#### XmlWriter への出力の送出  
 スタイル シートで `xsl:output` 要素が使用され、出力の種類が <xref:System.Xml.XmlWriter> オブジェクトの場合は、<xref:System.Xml.XmlWriter> オブジェクトを作成する際に <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=fullName> プロパティを使用します。  <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=fullName> プロパティは、コンパイル済みスタイル シートの `xsl:output` 要素から派生した情報を含む <xref:System.Xml.XmlWriterSettings> オブジェクトを返します。  この <xref:System.Xml.XmlWriterSettings> オブジェクトを <xref:System.Xml.XmlWriter.Create%2A?displayProperty=fullName> メソッドに渡して、正しい設定の <xref:System.Xml.XmlWriter> オブジェクトを作成することができます。  
  
## 出力の種類  
 次の一覧では、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> コマンドで使用できる出力の種類について説明します。  
  
#### XmlWriter  
 <xref:System.Xml.XmlWriter> クラスは XML ストリームまたはファイルを書き出します。  <xref:System.Xml.XmlWriterSettings> クラスを使用して、出力オプションも含め、<xref:System.Xml.XmlWriter> オブジェクトでサポートする機能を指定できます。  <xref:System.Xml.XmlWriter> クラスは <xref:System.Xml> フレームワークの重要な一部分です。  出力結果を別の XML プロセスにパイプラインして送るには、この出力を使用します。  
  
#### String  
 出力ファイルの URI を指定するには、この出力を使用します。  
  
#### ストリーム  
 ストリームとは、ファイル、入出力デバイス、プロセス間通信のパイプ、または TCP\/IP ソケットなどのバイト シーケンスを抽象化したものです。  <xref:System.IO.Stream> クラスとその派生クラスは、これら各種の入出力にジェネリックな視点を提供し、プログラマがオペレーティング システムや下位のデバイスに固有の詳細を考慮する必要をなくします。  
  
 <xref:System.IO.FileStream>、<xref:System.IO.MemoryStream>、または出力ストリーム \(`Response.OutputStream`\) にデータを送るには、この出力の種類を使用します。  
  
#### TextWriter  
 <xref:System.IO.TextWriter> は、文字シーケンスを書き出します。  これは <xref:System.IO.StringWriter> クラスおよび <xref:System.IO.StreamWriter> クラスに実装され、それぞれ文字を文字列に、またはストリームに書き出します。  文字列に出力する場合は、この出力の種類を使用します。  
  
## メモ  
  
-   空要素タグを書き出すとき、要素名の最後の文字とバック主ラッシュとの間に 1 つのスペースが書かれます。たとえば `<myElement />` です。  これにより、生成された HTML ページが古いブラウザーで正しく表示されます。  
  
## 参照  
 [XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations.md)