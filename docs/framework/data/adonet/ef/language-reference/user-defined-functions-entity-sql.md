---
title: "ユーザー定義関数 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ユーザー定義関数 (Entity SQL)
Entity SQL では、クエリ内でのユーザー定義関数の呼び出しがサポートされます。  これらの関数は、クエリでインラインで定義する \(「[How to: Call a User\-Defined Function](http://msdn.microsoft.com/ja-jp/ad131b86-8b4e-4747-8605-d4fc64fb9d02)」を参照\) ことも、概念モデルの一部として定義する \(「[How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/ja-jp/0dad7b8b-58f6-4271-b238-f34810d68e5f)」を参照\) こともできます。  概念モデル関数は、概念モデルの [Function](http://msdn.microsoft.com/ja-jp/dc3beca7-55cf-4977-8db0-5064cdbab134) 要素の [DefiningExpression](http://msdn.microsoft.com/ja-jp/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) 要素における Entity SQL コマンドとして定義されます。  
  
 Entity SQL を使用すると、関数をクエリ コマンド自体で定義することができます。  [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) 演算子は、インライン関数を定義します。  複数の関数を 1 つのコマンドで定義することができます。関数の署名が一意であれば、これら複数の関数に同じ名前を付けることができます。  詳細については、「[関数のオーバーロードの解決方法](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)」を参照してください。  
  
## 参照  
 [関数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)