---
title: "XML の処理オプション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18f8f9c76a1842517340eaa3f74b4778f869403e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-options"></a>XML の処理オプション
XML データの処理に使用できる Microsoft テクノロジの一覧については、次の表を参照してください。  
  
## <a name="net-framework-options"></a>.NET Framework のオプション  
  
|**オプション**|**処理の種類**|**説明**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> 名前空間)|メモリ内|-.NET Framework Language-Integrated クエリ (LINQ) テクノロジに基づいています。<br />-次のような SQL オブジェクト、リレーショナル データ、および XML データのクエリのエクスペリエンスを提供します。<br />機能を提供直観的なドキュメント作成および変換します。<br />-新しいコードを記述している場合は、このオプションを使用します。|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|ストリーム ベース|XML データにアクセスする高速、非キャッシュ、前方参照専用の方法を提供します。<br />-オブジェクトを作成できますを使用して、<xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType>メソッドを使用して、オブジェクトで有効にする機能のセットを指定し、<xref:System.Xml.XmlReaderSettings>クラスです。|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|ストリーム ベース|-高速、非キャッシュ、前方参照専用の XML データを生成する方法を提供します。<br />-オブジェクトを作成できますを使用して、<xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType>メソッドを使用して、オブジェクトで有効にする機能のセットを指定し、<xref:System.Xml.XmlWriterSettings>クラスです。|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|メモリ内|実装、 [W3C ドキュメント オブジェクト モデル (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html)と[DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/)の推奨事項です。<br />-できますを作成、挿入、削除、および使い慣れた DOM モデルに基づくメソッドとプロパティを使用してノードを変更します。<br />-W3C DOM を使用する既存のコードを変更する場合は、このオプションを使用します。|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|メモリ内|-複数の編集オプションとカーソル モデルを使用してナビゲーション機能を提供します。<br />XML ドキュメントに含まれていることができます、<xref:System.Xml.XPath.XPathDocument>または<xref:System.Xml.XmlDocument>オブジェクト。<br />-XML の読み取り専用の処理のための優れたパフォーマンスを提供します。<br />-既存のコードを XPath クエリや XSLT 変換を変更する場合は、このオプションを使用します。|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|メモリ内|-XSL 変換を使用して XML データを変換するためのオプションを提供します。<br />- [XSLT コンパイラ (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)を参照することができますが、アプリ内の変換を事前コンパイルされます。|  
  
## <a name="win32-and-com-based-options"></a>Win32 オプションと COM ベースのオプション  
  
|**オプション**|**説明**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|-高速、安全ですが、非キャッシュ、順方向専用の XML パーサーするのに役立つアプリの構築高性能な XML です。<br />のダイナミック リンク ライブラリ (Dll); を使用できる任意の言語と連携C++ を使用することをお勧めします。|  
|[MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|の Windows オペレーティング システムに含まれている XML を処理するため COM ベース テクノロジ。<br />-XPath と XSLT サポートと共に、DOM のネイティブな実装を提供します。<br />-SAX2 イベント ベース パーサーが含まれています。|  
  
## <a name="see-also"></a>関連項目  
 [DOM モデルを使用して XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [XPath データ モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XSLT コンパイラ (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
