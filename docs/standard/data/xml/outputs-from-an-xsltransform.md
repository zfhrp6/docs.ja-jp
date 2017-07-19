---
title: "XslTransform からの出力 | Microsoft Docs"
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
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XslTransform からの出力
スタイル シートは、`<xsl:output>` ステートメントと `method` 属性を使って出力形式を決定できます。次の表では、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して出力を書き出し、出力形式を <xref:System.IO.Stream> または <xref:System.IO.TextWriter> として宣言した場合に出力形式がどうなるかを説明します。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] では、<xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。  <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT \(Extensible Stylesheet Language for Transformations\) 変換を実行できます。  詳細については、「[XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)」を参照してください。  
  
 スタイル シートは、`<xsl:output>` ステートメントと `method` 属性を使って出力形式を決定できます。次の表では、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して出力を書き出し、出力形式を <xref:System.IO.Stream> または <xref:System.IO.TextWriter> として宣言した場合に出力形式がどうなるかを説明します。  <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを `<xsl:output>` ステートメントと共に使用して出力の種類を宣言した場合に得られる結果を次の表に示します。  
  
|\<xsl:output method \= \> attribute|結果の形式|  
|-----------------------------------------|-----------|  
|method\="xml"|XML|  
|method\="html"|HTML|  
|method\="text"|Text|  
  
> [!NOTE]
>  メモ: <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.Xml.XmlReader> または <xref:System.Xml.XmlWriter> である場合、`<xsl:output>` ステートメントは無視されます。  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.IO.Stream> または <xref:System.IO.TextWriter> である場合は、次の属性がサポートされます。  
  
-   encoding\*  
  
-   omit\-xml\-declaration  
  
-   スタンドアロン  
  
-   doctype\-public  
  
-   doctype\-system  
  
-   cdata\-section\-elements  
  
-   indent  
  
    > [!NOTE]
    >  \*<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドが出力を <xref:System.IO.TextWriter> に送信する場合、encoding 属性は無視されます。  その場合は、encoding 属性の代わりに <xref:System.IO.TextWriter> の encoding プロパティが使用されます。  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.IO.Stream> の場合、次の属性は無視されます。  
  
-   version : バージョンは常に 1.0 です。  
  
-   media\-type : メディア タイプです。  
  
## 特殊文字のエスケープ  
 `"<"` 記号の代わりに `<&lt>` を使用するなど、特殊文字を XML 形式にエスケープする必要があるかどうかを示すには、`<xsl:text disable-output-escaping>` タグを使用します。  <xref:System.Xml.XmlReader> オブジェクトまたは <xref:System.Xml.XmlWriter> オブジェクトへの変換では `disable-output-escaping` 属性が無視されるため、特殊文字はこのタグの影響を受けません。  
  
## 参照  
 [XslTransform クラスによる XSLT プロセッサの実装](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)