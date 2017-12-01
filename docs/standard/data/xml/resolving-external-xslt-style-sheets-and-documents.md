---
title: "外部の XSLT スタイル シートとドキュメントの解決"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5e84935f9fff1f993a677d408287cd775269f03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>外部の XSLT スタイル シートとドキュメントの解決
変換中には、外部リソースの解決が必要になるときがあります。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。 <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。  
  
 変換中には、外部リソースの解決が必要になるときがあります。  
  
-   <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時における外部スタイル シートの検索。  
  
-   <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時におけるスタイル シート内の `<xsl:include>` 要素または `<xsl:import>` 要素の解決。  
  
-   <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの実行時におけるすべての `document()` 関数の解決。  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver クラスの使い方  
 ネットワーク リソースにアクセスするのに認証が必要な場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> パラメーターを持っている <xref:System.Xml.XmlResolver> メソッドを使用して、必要な資格情報プロパティが設定された <xref:System.Xml.XmlResolver> オブジェクトを渡します。  
  
 独自の <xref:System.Xml.XmlResolver> を使用する場合や、異なる資格情報を指定する必要がある場合は、次の表に示すように、解決する必要のある外部リソースの処理に応じて、適切な作業を実行する必要があります。  
  
|解決する必要のある処理|必要な作業タスク|  
|--------------------------------------|-------------------|  
|<xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時におけるスタイル シートの検索。|スタイル シートが資格情報を必要とするリソース上にある場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> をパラメーターとして受け取るオーバーロードされた <xref:System.Xml.XmlResolver> メソッドを指定します。|  
|<xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時における `<xsl:include>` または `<xsl:import>` の解決。|<xref:System.Xml.Xsl.XslTransform.Load%2A> をパラメーターとして受け取るオーバーロードされた <xref:System.Xml.XmlResolver> メソッドを指定します。 <xref:System.Xml.XmlResolver> を使用して、`import` ステートメントまたは `include` ステートメントが参照しているスタイル シートを読み込みます。 `null` を渡すと、外部リソースは解決されません。|  
|変換中のすべての `document()` 関数の解決。|指定して、<xref:System.Xml.XmlResolver>を使用して、変換中に、<xref:System.Xml.Xsl.XslTransform.Transform%2A>を受け取るメソッド、<xref:System.Xml.XmlResolver>引数。|  
  
 `document()`関数の他の XML にリソースを取得、スタイル シートからさらに、入力ストリームで提供される XML 初期データ。 この関数には別の場所にある XML データを含めることができるため、<xref:System.Xml.XmlResolver> 値が設定された `null` を <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡すと、`document()` 関数は実行されません。 `document()` 関数を使用する場合は、適切なアクセス許可セットを取得したうえで、<xref:System.Xml.Xsl.XslTransform.Transform%2A> をパラメーターとして受け取る <xref:System.Xml.XmlResolver> メソッドを使用します。  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドと、このメソッドでの <xref:System.Xml.XmlResolver> の使い方の詳細については、「<xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>」を参照してください。  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを呼び出すと、読み込み時に指定された証拠に基づいてアクセス許可が計算され、そのアクセス許可セットが変換処理全体に割り当てられます。 `document()` 関数で、アクセス許可セットにないアクセス許可を必要とする処理を実行しようとすると、例外がスローされます。  
  
## <a name="see-also"></a>関連項目  
 [XslTransform クラスによる XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XslTransform クラスによる XSLT プロセッサ](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XslTransform からの出力](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
 [異なるストアでの XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
 [スタイル シート パラメーターと拡張オブジェクト用の XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
 [XSLT スタイル シートのスクリプトを使用して\<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
 [Msxsl:node-set() 関数のサポート](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
 [変換における XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [変換における XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [XslTransform への XPathDocument の入力](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [XslTransform への XmlDataDocument の入力](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [XslTransform への XmlDocument の入力](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
