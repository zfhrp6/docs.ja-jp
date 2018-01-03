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
ms.workload: dotnet
ms.openlocfilehash: 9d51ac97611379cc6c47ef698bc635bbf46d1e5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-related-data"></a>方法 : 関連データをフィルター処理する
取得したデータの量を制限するサブクエリを指定するには、<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドを使用します。  
  
## <a name="example"></a>例  
 次の例の <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドは、取得した `Orders` を、その日に出荷されていないものに限定します。 この処理を行わないと、サブセットのみが必要な場合でも、すべての `Orders` が取得されることになります。  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>参照  
 [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
