---
title: "方法 : 主キーを表す"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3510d52f6f6de9ee2e99ebc1e9fc6fa581d58f3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-primary-keys"></a>方法 : 主キーを表す
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>をデータベース列に主キーを表すフィールドまたはプロパティを指定する属性。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、計算列は主キーとしてサポートされません。  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>プロパティまたはフィールドを主キーとして指定するには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  値として `true` を指定します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
