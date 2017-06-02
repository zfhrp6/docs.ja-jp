---
title: "スキーマのインポートとエクスポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, スキーマのインポートとエクスポート"
  - "XsdDataContractExporter クラス"
  - "XsdDataContractImporter クラス"
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# スキーマのインポートとエクスポート
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]新しいシリアル化エンジンが含まれています、 <xref:System.Runtime.Serialization.DataContractSerializer>します。 `DataContractSerializer` は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] オブジェクトと XML を双方向で変換します。 このシリアライザー自体の他に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、関連するスキーマ インポート機構とスキーマ エクスポート機構が用意されています。 *スキーマ*シリアライザーが生成するか、デシリアライザーがアクセスできる、または XML の形状の正式かつ正確であり、コンピューターが認識できる説明を示します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、多数のサードパーティ プラットフォームとの広範な相互運用性を持つ W3C (World Wide Web Consortium) XML スキーマ定義言語 (XSD: XML Schema Definition Language) をスキーマ表現として使用します。  
  
 スキーマ インポート コンポーネント<xref:System.Runtime.Serialization.XsdDataContractImporter>、XSD スキーマ ドキュメントを取得、および生成[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]クラス (通常、データ コントラクト クラス) をシリアル化された形式が特定のスキーマに対応するようにします。  
  
 たとえば、次のスキーマ フラグメントがあるとします。  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 これは、読みやすいように、やや簡素化された次の型を生成します。  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 生成された型がいくつかのデータ コントラクトのベスト プラクティスを準拠していることに注意してください (で見つかった[ベスト プラクティス: データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md))。  
  
-   型が実装、 <xref:System.Runtime.Serialization.IExtensibleDataObject>インターフェイスです。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)します。  
  
-   データ メンバーは、プライベート フィールドをラップするパブリック プロパティとして実装されます。  
  
-   クラスは部分クラスであり、生成されたコードを変更せずに追加を行うことができます。  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>逆を行うことができます-によってシリアル化できる型を受け取る、 `DataContractSerializer` XSD スキーマ ドキュメントを生成します。  
  
## <a name="fidelity-is-not-guaranteed"></a>忠実性は保証されない  
 スキーマや型のラウンド トリップでの完全な忠実性は保証されません  (A*ラウンド トリップ*クラスのセットを作成し、もう一度スキーマを作成する結果をエクスポートするスキーマをインポートすることを意味します)。同じスキーマが返されない場合があります。 また、これとは逆のプロセスでも忠実性は保証されません  (スキーマを生成する型をエクスポートしてから、型をインポートし直す場合です。 この場合も、同じ型が返されない可能性があります)。  
  
## <a name="supported-types"></a>サポートされている型  
 データ コントラクト モデルは、WC3 スキーマの限られたサブセットしかサポートしません。 このサブセットに準拠しないスキーマを使用すると、インポート プロセスで例外が発生します。 たとえば、データ コントラクトのデータ メンバーを XML 属性としてシリアル化するように指定することはできません。 したがって、XML 属性を使用する必要があるスキーマはサポートされず、適切な XML 投影を持つデータ コントラクトを生成できないため、インポート時に例外が発生します。  
  
 たとえば、次のスキーマ フラグメントは、既定のインポート設定を使用してインポートすることはできません。  
  
 <!-- TODO: review snippet reference [!code[c_SchemaImportExport#9](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  -->  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト スキーマ リファレンス](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)します。 スキーマがデータ コントラクト ルールに準拠していない場合は、別のシリアル化エンジンを使用します。 たとえば、 <xref:System.Xml.Serialization.XmlSerializer>独自のスキーマ インポート機構を使用します。 また、サポートされるスキーマの範囲を拡張する特別なインポート モードもあります。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]生成に関するセクション<xref:System.Xml.Serialization.IXmlSerializable>型[クラスを生成するには、スキーマのインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)します。  
  
 `XsdDataContractExporter` は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] によってシリアル化できるすべての `DataContractSerializer` 型をサポートします。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト シリアライザーでサポートされる型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)します。 使用して作成されたそのスキーマ、`XsdDataContractExporter`通常有効なデータを`XsdDataContractImporter`使用できます (しない限り、 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>スキーマをカスタマイズするために使用)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用して、 <xref:System.Runtime.Serialization.XsdDataContractImporter>を参照してください[クラスを生成するには、スキーマのインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)します。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用して、 <xref:System.Runtime.Serialization.XsdDataContractExporter>を参照してください[クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 [クラスを生成するスキーマをインポートします。](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)   
 [クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)