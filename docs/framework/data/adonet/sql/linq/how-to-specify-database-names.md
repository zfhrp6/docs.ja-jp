---
title: "How to: Specify Database Names | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Specify Database Names
<xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性の <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> プロパティを使用すると、接続によってデータベースの名前が提供されない場合に、名前を指定できます。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>」を参照してください。  
  
### データベースの名前を指定するには  
  
1.  データベースのクラス宣言に <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性を追加します。  
  
2.  <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性に <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> プロパティを追加します。  
  
3.  <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> プロパティ値を目的の名前に設定します。  
  
## 参照  
 [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [How to: Customize Entity Classes by Using the Code Editor](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)