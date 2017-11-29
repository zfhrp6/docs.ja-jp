---
title: "方法 : 関連データをフィルター処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f02b09cc5389a90ea42a0dd851579327972c20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-related-data"></a>方法 : 関連データをフィルター処理する
取得したデータの量を制限するサブクエリを指定するには、<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドを使用します。  
  
## <a name="example"></a>例  
 次の例の <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドは、取得した `Orders` を、その日に出荷されていないものに限定します。 この処理を行わないと、サブセットのみが必要な場合でも、すべての `Orders` が取得されることになります。  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [データベースの照会](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
