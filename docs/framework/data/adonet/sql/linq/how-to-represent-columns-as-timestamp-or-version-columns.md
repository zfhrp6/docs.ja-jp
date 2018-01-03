---
title: "方法 : 列をタイムスタンプ列またはバージョン列として表現する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 465be5cc0125d0ac45c0a00d7f1f238f3de8a390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>方法 : 列をタイムスタンプ列またはバージョン列として表現する
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>のプロパティ、<xref:System.Data.Linq.Mapping.ColumnAttribute>データベース タイムスタンプまたはバージョン番号を保持するデータベース列を表すフィールドまたはプロパティを指定する属性。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>」を参照してください。  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>タイムスタンプ列またはバージョン列を表すフィールドまたはプロパティを指定するには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> プロパティ値を `true` に設定します。  
  
## <a name="see-also"></a>参照  
 [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [方法 : 同時実行の競合を検査するメンバーを指定する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [方法 : コード エディターを使用してエンティティ クラスをカスタマイズする](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
