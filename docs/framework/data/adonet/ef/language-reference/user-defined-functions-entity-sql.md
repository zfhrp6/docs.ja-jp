---
title: "ユーザー定義関数 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e5cfc9685c1e088722b24b54b4a0368d52fda29
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="user-defined-functions-entity-sql"></a>ユーザー定義関数 (Entity SQL)
Entity SQL では、クエリ内でのユーザー定義関数の呼び出しがサポートされます。 関数をインライン クエリでこれらを定義することができます (を参照してください[する方法: ユーザー定義関数を呼び出す](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) または概念モデルの一部として (を参照してください[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f))。 Entity SQL コマンドを概念モデル関数が定義されている、 [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e)の要素、[関数](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134)概念モデル内の要素。  
  
 Entity SQL を使用すると、関数をクエリ コマンド自体で定義することができます。 [関数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)演算子は、インライン関数を定義します。 複数の関数を 1 つのコマンドで定義することができます。関数の署名が一意であれば、これら複数の関数に同じ名前を付けることができます。 詳細については、「 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
