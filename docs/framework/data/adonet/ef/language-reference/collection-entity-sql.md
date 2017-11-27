---
title: COLLECTION (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8d078749d20740cdade323edab975ce221e72cfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="collection-entity-sql"></a>COLLECTION (Entity SQL)
COLLECTION キーワードは、インライン関数を定義する場合にのみ使用します。 コレクション関数は、値のコレクションを操作してスカラー出力を生成する関数です。  
  
## <a name="syntax"></a>構文  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>引数  
 `type_definition`  
 サポートされる型、行、または参照のコレクションを返す式。  
  
## <a name="remarks"></a>コメント  
 COLLECTION キーワードについて詳しくは、「 [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例は、COLLECTION キーワードを使用して 10 進数のコレクションをインライン クエリ関数の引数として宣言する方法を示します。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
