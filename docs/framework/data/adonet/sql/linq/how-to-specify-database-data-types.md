---
title: "方法 : データベース データ型を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 17ac588a8cf6815b244cf0b515603263f41b53ad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-specify-database-data-types"></a>方法 : データベース データ型を指定する
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>属性を T-SQL テーブル宣言内で列を定義する正確なテキストを指定します。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティは、<xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してデータベースのインスタンスを作成することを予定している場合のみ指定する必要があります。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>」を参照してください。  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>データ型を T-SQL テーブルに定義するテキストを指定するには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティの値を T-SQL で使用される正確なテキストに設定します。  
  
## <a name="see-also"></a>参照  
 [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [方法 : コード エディターを使用してエンティティ クラスをカスタマイズする](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
