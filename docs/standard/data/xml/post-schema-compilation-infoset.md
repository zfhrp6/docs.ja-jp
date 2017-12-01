---
title: "スキーマのコンパイル後の情報セット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77fe1790a4ff2f910a740e969e458549f1fd9642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="post-schema-compilation-infoset"></a>スキーマのコンパイル後の情報セット
[World Wide Web Consortium (W3C) XML スキーマ勧告](http://go.microsoft.com/fwlink/?linkid=45242)情報セット (infoset) スキーマ検証前とスキーマ コンパイル後に公開する必要があります。 XML スキーマ オブジェクト モデル (SOM) は、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドが呼び出される前と後について、この公開内容を調べます。  
  
 スキーマの検証前の情報セットは、スキーマの編集時に作成されます。 スキーマ コンパイル後の情報セットは、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドが呼び出された後、スキーマのコンパイル時に生成され、プロパティとして公開されます。  
  
 SOM はスキーマ検証前とスキーマ コンパイル後の情報セットを表すオブジェクト モデルです。これは <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間内のクラスで構成されます。 <xref:System.Xml.Schema> 名前空間内のクラスの読み書き可能なプロパティは、すべてスキーマ検証前の情報セットに属し、一方 <xref:System.Xml.Schema> 名前空間のクラスの読み取り専用プロパティは、すべてスキーマ コンパイル後の情報セットに属します。 この規則の例外は、スキーマ検証前の情報セットとスキーマ コンパイル後の情報セットの両方のプロパティである、次のプロパティです。  
  
|クラス|プロパティ|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 たとえば、<xref:System.Xml.Schema.XmlSchemaElement> クラスと <xref:System.Xml.Schema.XmlSchemaComplexType> クラスには `BlockResolved` プロパティと `FinalResolved` プロパティがあります。 これらのプロパティは、スキーマがコンパイルおよび検証された後に、`Block` プロパティと `Final` プロパティの値を格納するために使用されます。 `BlockResolved` プロパティと `FinalResolved` プロパティは、スキーマ コンパイル後の情報セットの一部であり、読み取り専用のプロパティです。  
  
 スキーマの検証後に設定される <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> クラスの <xref:System.Xml.Schema.XmlSchemaElement> プロパティを次の例に示します。 検証の前の時点では、このプロパティには `null` 参照が含まれており、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> には問題の型の名前が設定されています。 検証後、<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> は有効な型に解決され、型オブジェクトは <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> プロパティを通じて利用できます。  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [XML スキーマ オブジェクト モデル (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
