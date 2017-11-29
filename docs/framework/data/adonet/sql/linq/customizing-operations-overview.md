---
title: "操作のカスタマイズの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7653ca137c93da5174e0ddcd1ced8bdfceaa9edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-overview"></a>操作のカスタマイズの概要
既定では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、対応付けに基づいて、挿入、更新、および削除の各操作のための動的な SQL を生成します。 しかし実際には、セキュリティや検証などを目的とした独自のビジネス ロジックを追加することが必要になる場合がよくあります。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]これらの操作をカスタマイズするための手法には、次の項目が含まれます。  
  
## <a name="loading-options"></a>読み込みオプション  
 クエリで、データベースに接続するときに、メイン ターゲットに関係するデータをどれだけ取得するかを制御できます。 この機能は主に、<xref:System.Data.Linq.DataLoadOptions> を使用して実装します。 詳細については、次を参照してください。[遅延実行と即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)です。  
  
## <a name="partial-methods"></a>部分メソッド  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による既定の対応付けでは、ビジネス ロジックの実装に使用できる部分メソッドが提供されます。 詳細については、次を参照してください。[を追加するビジネス ロジックでメソッドを使用して部分](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)です。  
  
## <a name="stored-procedures-and-user-defined-functions"></a>ストアド プロシージャおよびユーザー定義関数  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ストアド プロシージャおよびユーザー定義関数の使用をサポートしています。 ストアド プロシージャは、操作のカスタマイズによく使用されます。 詳細については、「[ストアド プロシージャ](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [カスタマイズの挿入、更新、および Delete 操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
