---
title: "XML スキーマの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e21d402dce02ecb332d041f0cda651df911979ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-xml-schemas"></a>XML スキーマの使用
XML ドキュメントの構造、その要素間のリレーションシップ、データ型、および内容の制約を定義するには、ドキュメント型定義 (DTD: Document Type Definition) または XML スキーマ定義言語 (XSD) スキーマを使用します。 XML ドキュメントは、W3C (World Wide Web Consortium) 勧告『Extensible Markup Language (XML) 1.0』で定義されている構文要件をすべて満たしている場合には整形式と見なされますが、整形式であると同時に DTD またはスキーマに定義されている制約に準拠していなければ有効とは見なされません。 したがって、有効な XML ドキュメントはすべて整形式ですが、整形式の XML ドキュメントがすべて有効であるとは限りません。  
  
 XML の詳細については、次を参照してください。、 [w3c 勧告 『 XML 1.0 』](http://go.microsoft.com/fwlink/?linkid=7269)です。 XML スキーマの詳細については、次を参照してください。、 [W3C XML Schema Part 1: Structures](http://go.microsoft.com/fwlink/?linkid=48881)と[W3C XML Schema Part 2: Datatypes recommendation 』](http://go.microsoft.com/fwlink/?linkid=17392)の推奨事項です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ オブジェクト モデル (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間のスキーマ オブジェクト モデル (SOM) について説明します。SOM は、ファイルからスキーマ定義言語 (XSD) スキーマを読み取ったり、プログラムを使用してメモリ内にスキーマを作成したりできる一連のクラスを提供します。  
  
 [スキーマのコンパイルのための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <xref:System.Xml.Schema.XmlSchemaSet> クラスについて説明します。このクラスは、XSD スキーマを格納または検証できるキャッシュです。  
  
 [XmlSchemaValidator のプッシュ ベースの検証](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <xref:System.Xml.Schema.XmlSchemaValidator> クラスについて説明します。このクラスは、プッシュ ベース方式で、XSD スキーマを基準として XML データを検証する、効率的かつ高性能なしくみを提供します。  
  
 [XML スキーマの推論](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <xref:System.Xml.Schema.XmlSchemaInference> クラスを使用して XML ドキュメントの構造から XSD スキーマを推論する方法を説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>関連項目  
 [DOM における XML ドキュメントの検証](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 ドキュメント オブジェクト モデル (DOM) の XML を検証する方法を説明します。 検証できる XML は、DOM に読み込まれている XML か、または事前に検証されていない DOM の XML ドキュメントです。  
  
 [XPathNavigator を使用するスキーマの検証](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <xref:System.Xml.XPath.XPathNavigator> クラスを使用して操作中および編集中の XML を検証する方法を説明します。
