---
title: 入れ子になったグループの作成
description: 入れ子になったグループを作成する方法。
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="create-a-nested-group"></a>入れ子になったグループの作成

LINQ クエリ式で入れ子になったグループを作成する方法を次の例に示します。 学年レベルに基づいて作成した各グループを、さらに個人の名前に基づくグループに分割します。  
  
## <a name="example"></a>例

 > [!NOTE]
 > この例には、「[オブジェクトのコレクションの照会](query-a-collection-of-objects.md)」のサンプル コードで定義されているオブジェクトへの参照が含まれています。 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 入れ子になったグループの内部要素に対して反復処理を実行するために、入れ子になった `foreach` ループが 3 つ必要であることに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)
