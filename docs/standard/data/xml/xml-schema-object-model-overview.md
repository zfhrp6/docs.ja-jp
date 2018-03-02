---
title: "XML スキーマ オブジェクト モデルの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e18a3151228ea7edb5a8380f6ed707ee88d369e5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-object-model-overview"></a>XML スキーマ オブジェクト モデルの概要
Microsoft .NET Framework のスキーマ オブジェクト モデル (SOM) は豊富な機能を備えた API で、スキーマの作成、編集、および検証をプログラムで実行できます。 SOM は、ドキュメント オブジェクト モデル (DOM) が XML ドキュメント上で機能するのと同様に、XML スキーマ ドキュメント上で機能します。 XML スキーマ ドキュメントは有効な XML ファイルで、SOM に読み込まれると、スキーマに準拠した他の XML ドキュメントの構造および有効性に関する情報を伝えます。  
  
 スキーマは、特定のスキーマに対して XML ドキュメントの構造またはモデルを指定することによって XML ドキュメントのクラスを定義する、XML ドキュメントです。 スキーマは、XML ドキュメントの内容に対する制約を指定し、特定のスキーマと照合して有効と見なされるように、規定に準拠した XML ドキュメントが従う表現形式 (規則または文法) を記述します。 XML ドキュメントの検証は、ドキュメントがスキーマによって指定された文法に準拠しているかどうかを確認するプロセスです。  
  
 .NET Framework の SOM API を使用すると、スキーマの作成、編集、および検証に関する次の操作を行うことができます。  
  
-   有効なスキーマをファイルから読み込み、ファイルへ保存します。  
  
-   厳密に型指定されたクラスを使用し、メモリ内にスキーマを作成します。  
  
-   <xref:System.Xml.Schema.XmlSchemaSet> クラスと対話し、スキーマのキャッシュ、コンパイル、および取得を行います。  
  
-   <xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドと対話し、スキーマを基準として XML インスタンス ドキュメントを検証します。  
  
-   スキーマの作成および保守に使用するエディターを作成します。  
  
-   XML インスタンス ドキュメントの検証で使用するためにコンパイルと保存が可能なスキーマを動的に編集します。  
  
## <a name="the-schema-object-model"></a>スキーマ オブジェクト モデル  
 SOM は、XML スキーマの要素に相当する <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間の広範囲にわたるクラスで構成されています。 たとえば、`<xsd:schema>...</xsd:schema>` 要素は <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> クラスにマップしているため、`<xsd:schema/>` 要素に格納できる情報はすべて <xref:System.Xml.Schema.XmlSchema> クラスを使って表すことができます。 同様に、`<xsd:element>...</xsd:element>` 要素と `<xsd:attribute>...</xsd:attribute>` 要素は、それぞれ <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> クラスと <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> クラスにマップしています。 このマッピングは、次の図に示す <xref:System.Xml.Schema> 名前空間の XML スキーマ オブジェクト モデルを作成する XML スキーマのすべての要素に適用されます。  
  
 ![System.Xml.Schema オブジェクト モデル](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 <xref:System.Xml.Schema> 名前空間の各クラスの詳細については、.NET Framework クラス ライブラリの <xref:System.Xml.Schema> 名前空間のリファレンス ドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [XML スキーマの読み取りと書き込み](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [XML スキーマの作成](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML スキーマの走査](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML スキーマの編集](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XML スキーマのインクルードまたはインポート](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [スキーマをコンパイルするための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [スキーマのコンパイル後の情報セット](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
