---
title: "XslTransform クラスからの移行 | Microsoft Docs"
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
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XslTransform クラスからの移行
XSLT アーキテクチャは、[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] リリースで設計が変更されました。  <xref:System.Xml.Xsl.XslTransform> クラスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスで置き換えられています。  
  
 以降では、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと <xref:System.Xml.Xsl.XslTransform> クラスの主な相違点について説明します。  
  
## パフォーマンス テスト  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスでは多くのパフォーマンスの向上が図られています。  新しい XSLT プロセッサは XSLT スタイル シートを、共通言語ランタイム \(CLR\) が他のプログラム言語で行うのと同様に、共通の中間形式にコンパイルします。  いったんスタイル シートがコンパイルされると、それをキャッシュして再利用することができます。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスには、このクラスを <xref:System.Xml.Xsl.XslTransform> クラスよりも大幅に高速化する他の最適化も含まれています。  
  
> [!NOTE]
>  全体的なパフォーマンスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスの方が <xref:System.Xml.Xsl.XslTransform> クラスより優れていますが、<xref:System.Xml.Xsl.XslCompiledTransform> クラスの <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドが変換で初めて呼び出されたときは、<xref:System.Xml.Xsl.XslTransform> クラスの <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドよりパフォーマンスが劣る場合があります。  これは、XSLT ファイルを読み込む前にコンパイルする必要があるためです。  詳細については、ブログの投稿「[XslCompiledTransform は XslTransform より遅い?](http://go.microsoft.com/fwlink/?LinkId=130590)」を参照してください。  
  
## セキュリティ  
 既定で、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでは XSLT `document()` 関数と埋め込みスクリプトのサポートが無効になっています。  これらの機能を有効にするには、機能が有効になっている <xref:System.Xml.Xsl.XsltSettings> オブジェクトを作成し、それを <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドに渡します。  スクリプト作成を有効にして XSLT 変換を実行する方法を次の例に示します。  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 詳細については、「[XSLT のセキュリティに関する考慮事項](../../../../docs/standard/data/xml/xslt-security-considerations.md)」を参照してください。  
  
## 新機能  
  
### 一時テーブル  
 XSLT の処理中に一時ファイルが生成されることがあります。  スタイル シートにスクリプト ブロックが含まれる場合、またはデバッグ設定を true に設定してスタイル シートをコンパイルした場合、%TEMP% フォルダーに一時ファイルが作成されます。  タイミングの問題で、一部の一時ファイルが削除されない場合があります。  たとえば、一時ファイルが現在の AppDomain やデバッガーにより使用されると、<xref:System.CodeDom.Compiler.TempFileCollection> オブジェクトの終了処理でそのファイルを削除できなくなります。  
  
 クライアントのすべての一時ファイルが削除されるように、<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> プロパティを使用して追加のクリーンアップを実行することができます。  
  
### xsl:output 要素と XmlWriter のサポート  
 変換出力が <xref:System.Xml.XmlWriter> オブジェクトに送られる場合、<xref:System.Xml.Xsl.XslTransform> クラスでは `xsl:output` の設定が無視されていました。  <xref:System.Xml.Xsl.XslCompiledTransform> クラスには、スタイル シートの `xsl:output` 要素から取得された出力情報を含む <xref:System.Xml.XmlWriterSettings> オブジェクトを返す <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> プロパティがあります。  <xref:System.Xml.XmlWriterSettings> オブジェクトを使用して、適切に設定された <xref:System.Xml.XmlWriter> オブジェクトを作成し、それを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡すことができます。  次の C\# コードに、この処理を示します。  
  
```  
// Create the XslTransform object and load the style sheet.  
XslCompiledTransform xslt = new XslCompiledTransform();  
xslt.Load(stylesheet);  
  
// Load the file to transform.  
XPathDocument doc = new XPathDocument(filename);  
  
// Create the writer.  
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);  
  
// Transform the file and send the output to the console.  
xslt.Transform(doc, writer);  
writer.Close();  
```  
  
### デバッグ オプション  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスによりデバッグ情報を生成できます。この機能を利用して、Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] デバッガーを使用してスタイル シートをデバッグすることができます。  詳細については、「<xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>」を参照してください。  
  
## 動作の違い  
  
### XmlReader への変換  
 <xref:System.Xml.Xsl.XslTransform> クラスには、変換結果を <xref:System.Xml.XmlReader> オブジェクトとして返す Transform オーバーロードが数種類あります。  このオーバーロードを使用することで、生成される XML ツリーのシリアル化と逆シリアル化によるオーバーヘッドを生じることなく、変換結果をメモり内表現 \(<xref:System.Xml.XmlDocument> または <xref:System.Xml.XPath.XPathDocument>\) に読み込むことができます。  次の C\# コード例で、<xref:System.Xml.XmlDocument> オブジェクトに変換結果を読み込む方法を示します。  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、<xref:System.Xml.XmlReader> オブジェクトへの変換がサポートされません。  ただし、<xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> メソッドを使用して、生成される XML ツリーを <xref:System.Xml.XmlWriter> から直接読み込むことはできます。  次の C\# コード例では、同じ操作を <xref:System.Xml.Xsl.XslCompiledTransform> を使用して行う方法を示します。  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### 随意動作  
 W3C 勧告『XSL Transformations \(XSLT\) Version 1.0』には、対処方法を実装者が決定できる事項があります。  このような事項は、随意動作と見なされています。  事項によっては、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと <xref:System.Xml.Xsl.XslTransform> クラスで動作が異なります。  詳細については、「[XSLT エラーの解決](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)」を参照してください。  
  
### 拡張オブジェクトとスクリプト関数  
 <xref:System.Xml.Xsl.XslCompiledTransform> では、スクリプト関数の使用に関して新たに 2 つの制限が加えられています。  
  
-   XPath 式からはパブリック メソッドのみを呼び出すことができる。  
  
-   オーバーロードは引数の数に基づいて区別される。  引数の数が同じオーバーロードが複数存在する場合、例外が発生します。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> では、スクリプト関数へのバインド \(メソッド名参照\) がコンパイル時に実行されます。XslTranform を利用するスタイル シートを <xref:System.Xml.Xsl.XslCompiledTransform> によって読み込むと、例外が発生する場合があります。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> では、`msxsl:script` 要素内に子要素として `msxsl:using` および `msxsl:assembly` を含めることがサポートされます。  `msxsl:using` 要素と `msxsl:assembly` 要素を使用して、スクリプト ブロックで使用する追加の名前空間とアセンブリを宣言できます。  詳細については、「[msxsl:script を使用したスクリプト ブロック](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)」を参照してください。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> では、複数のオーバーロードおよびそれと同数の引数を含む拡張オブジェクトは使用できません。  
  
### MSXML 関数  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、新しい MSXML 関数のサポートが追加されました。  新しい関数または強化された関数は次のとおりです。  
  
-   msxsl:node\-set : <xref:System.Xml.Xsl.XslTransform> では、[node\-set 関数](http://msdn.microsoft.com/ja-jp/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) 関数の引数を結果ツリー フラグメントにする必要がありました。  <xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、この要件がありません。  
  
-   msxsl:version : この関数は、<xref:System.Xml.Xsl.XslCompiledTransform> でサポートされます。  
  
-   XPath 拡張関数 : [ms:string\-compare 関数](http://msdn.microsoft.com/ja-jp/20616b82-9e27-444c-b714-4f1e09b73aee)、[ms:utc 関数](http://msdn.microsoft.com/ja-jp/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f)、[ms:namespace\-uri 関数](http://msdn.microsoft.com/ja-jp/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7)、[ms:local\-name 関数](http://msdn.microsoft.com/ja-jp/10ed60a1-17a9-4d74-8b98-7940ac97c0b5)、[ms:number 関数](http://msdn.microsoft.com/ja-jp/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954)、[ms:format\-date 関数](http://msdn.microsoft.com/ja-jp/51f35609-89a9-4098-a166-88bf01300bf5)、および [ms:format\-time 関数](http://msdn.microsoft.com/ja-jp/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) の各関数が新たにサポートされました。  
  
-   スキーマ関連の XPath 拡張関数 : これは、<xref:System.Xml.Xsl.XslCompiledTransform> ではネイティブでサポートされません。  ただし、拡張関数として実装することはできます。  
  
## 参照  
 [XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations.md)   
 [XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)