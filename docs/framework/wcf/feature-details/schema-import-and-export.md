---
title: "スキーマのインポートとエクスポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c6d4917cc34021381e30d45b50b225b6aa4d18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="schema-import-and-export"></a>スキーマのインポートとエクスポート
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には新しいシリアル化エンジン、 <xref:System.Runtime.Serialization.DataContractSerializer>が含まれます。 `DataContractSerializer` は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] オブジェクトと XML を双方向で変換します。 このシリアライザー自体の他に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、関連するスキーマ インポート機構とスキーマ エクスポート機構が用意されています。 *スキーマ*シリアライザーが生成するか、デシリアライザーがアクセスできる、または XML の形状の正式かつ正確であり、コンピューターが判読できる説明を示します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、多数のサードパーティ プラットフォームとの広範な相互運用性を持つ W3C (World Wide Web Consortium) XML スキーマ定義言語 (XSD: XML Schema Definition Language) をスキーマ表現として使用します。  
  
 スキーマ インポート コンポーネント <xref:System.Runtime.Serialization.XsdDataContractImporter> は、XSD スキーマ ドキュメントを受け取って、シリアル化された形式が特定のスキーマに対応するように [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] クラス (通常、データ コントラクト クラス) を生成します。  
  
 たとえば、次のスキーマ フラグメントがあるとします。  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 これは、読みやすいように、やや簡素化された次の型を生成します。  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 生成された型がいくつかのデータ コントラクトのベスト プラクティスに従うことに注意してください (で見つかった[ベスト プラクティス: データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md))。  
  
-   この型は <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)です。  
  
-   データ メンバーは、プライベート フィールドをラップするパブリック プロパティとして実装されます。  
  
-   クラスは部分クラスであり、生成されたコードを変更せずに追加を行うことができます。  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> では反転を実行できます。つまり、`DataContractSerializer` によってシリアル化できる型を受け取って XSD スキーマ ドキュメントを生成できます。  
  
## <a name="fidelity-is-not-guaranteed"></a>忠実性は保証されない  
 スキーマや型のラウンド トリップでの完全な忠実性は保証されません  (A*ラウンド トリップ*クラスのセットを作成し、もう一度スキーマを作成する結果をエクスポートするスキーマをインポートすることを意味します)。同じスキーマが返されない場合があります。 また、これとは逆のプロセスでも忠実性は保証されません  (スキーマを生成する型をエクスポートしてから、型をインポートし直す場合です。 この場合も、同じ型が返されない可能性があります)。  
  
## <a name="supported-types"></a>サポートされている型  
 データ コントラクト モデルは、WC3 スキーマの限られたサブセットしかサポートしません。 このサブセットに準拠しないスキーマを使用すると、インポート プロセスで例外が発生します。 たとえば、データ コントラクトのデータ メンバーを XML 属性としてシリアル化するように指定することはできません。 したがって、XML 属性を使用する必要があるスキーマはサポートされず、適切な XML 投影を持つデータ コントラクトを生成できないため、インポート時に例外が発生します。  
  
 たとえば、次のスキーマ フラグメントは、既定のインポート設定を使用してインポートすることはできません。  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト スキーマ リファレンス](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)です。 スキーマがデータ コントラクト ルールに準拠していない場合は、別のシリアル化エンジンを使用します。 たとえば、<xref:System.Xml.Serialization.XmlSerializer> は、独自のスキーマ インポート機構を使用します。 また、サポートされるスキーマの範囲を拡張する特別なインポート モードもあります。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]生成に関するセクション<xref:System.Xml.Serialization.IXmlSerializable>型[クラスを生成するには、スキーマのインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)です。  
  
 `XsdDataContractExporter` は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] によってシリアル化できるすべての `DataContractSerializer` 型をサポートします。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト シリアライザーでサポートされる型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)です。 通常、`XsdDataContractExporter` を使用して作成されたスキーマは、`XsdDataContractImporter` を使用してカスタマイズしない限り、<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> で使用できる有効なデータです。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用して、<xref:System.Runtime.Serialization.XsdDataContractImporter>を参照してください[クラスを生成するには、スキーマのインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)です。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用して、<xref:System.Runtime.Serialization.XsdDataContractExporter>を参照してください[クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [クラスを生成するスキーマのインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
