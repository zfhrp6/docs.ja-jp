---
title: '方法 : コード エディターを使用してエンティティ クラスをカスタマイズする'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f57b07d03297347561b6b2e2634038aa1f29bc40
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a>方法 : コード エディターを使用してエンティティ クラスをカスタマイズする
Visual Studio を使用している開発者が使用できる、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を作成または、そのエンティティ クラスをカスタマイズします。  
  
 独自のマッピング コードを記述するか、既に生成されているコードをカスタマイズするには、また、Visual Studio コード エディターを使用することができます。 詳細については、次を参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。  
  
 このセクションのトピックでは、オブジェクト モデルをカスタマイズする方法について説明します。  
  
 [方法 : データベースの名前を指定する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> の使用方法について説明します。  
  
 [方法 : クラスとしてテーブルを表す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <xref:System.Data.Linq.Mapping.TableAttribute> の使用方法について説明します。  
  
 [方法 : クラス メンバーとして列を表す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> の使用方法について説明します。  
  
 [方法 : 主キーを表す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> の使用方法について説明します。  
  
 [方法 : データベース リレーションシップを割り当てる](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性の使い方の例を示します。  
  
 [方法 : 列をデータベース生成列として表す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> の使用方法について説明します。  
  
 [方法 : 列をタイムスタンプ列またはバージョン列として表現する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> の使用方法について説明します。  
  
 [方法 : データベース データ型を指定する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> の使用方法について説明します。  
  
 [方法 : 計算列を表す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> の使用方法について説明します。  
  
 [方法 : プライベート ストレージ フィールドを指定する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> の使用方法について説明します。  
  
 [方法 : null 値を許可する列として列を表す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> の使用方法について説明します。  
  
 [方法 : 継承階層を割り当てる](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 継承階層の指定に必要な割り当てについて説明します。  
  
 [方法 : 同時実行の競合のチェックを指定する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> の使用方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
