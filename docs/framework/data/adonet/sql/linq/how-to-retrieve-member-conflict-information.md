---
title: "方法 : メンバーの競合情報を取得する"
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
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9dd92ad1b5c91798923296def8f207637b4bad2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-member-conflict-information"></a>方法 : メンバーの競合情報を取得する
<xref:System.Data.Linq.MemberChangeConflict> クラスを使用すると、競合する個々のメンバーに関する情報を取得できます。 この同じコンテキストで、メンバーの競合の処理をカスタマイズできます。 詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。  
  
## <a name="example"></a>例  
 次のコードでは、<xref:System.Data.Linq.ObjectChangeConflict> オブジェクトを反復処理します。 オブジェクトごとに、次に <xref:System.Data.Linq.MemberChangeConflict> オブジェクトを反復処理します。  
  
> [!NOTE]
>  <xref:System.Reflection> 情報を提供するには、<xref:System.Data.Linq.MemberChangeConflict.Member%2A> を含めます。  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>参照  
 [方法 : 変更の競合を管理する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
