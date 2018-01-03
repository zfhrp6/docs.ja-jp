---
title: "ユーザー定義関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 833ffbbccfb35fd51ddde5dbeb4e3de3d79923ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="user-defined-functions"></a>ユーザー定義関数
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、オブジェクト モデル内のメソッドを使用して、ユーザー定義関数を表します。 <xref:System.Data.Linq.Mapping.FunctionAttribute> 属性、および必要に応じて <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を適用することによって、メソッドを関数として指定します。 詳細については、次を参照してください。 [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)です。  
  
 <xref:System.InvalidOperationException> を回避するため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で作成するユーザー定義関数は次のいずれかの形式にする必要があります。  
  
-   正しいマッピング属性を持つメソッド呼び出しとしてラップされた関数。 詳細については、次を参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に固有の静的 SQL メソッド。  
  
-   [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] メソッドによってサポートされる関数。  
  
 このセクションのトピックでは、自分でコードを作成する場合に、アプリケーション内でこれらのメソッドを記述および呼び出す方法について説明します。 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している開発者は、通常、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用してユーザー定義関数を対応付けます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : スカラー値のユーザー定義関数を使用する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 スカラー値を返す関数を実装する方法を説明します。  
  
 [方法 : テーブル値のユーザー定義関数を使用する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 テーブル値を返す関数を実装する方法を説明します。  
  
 [方法 : ユーザー定義関数をインラインで呼び出す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 関数をインラインで呼び出す方法とインライン呼び出しの実行時の相違点について説明します。
