---
title: "空間関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: acc09f9ea83e42377d0ba633927ecef13d5f46a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="spatial-functions"></a>空間関数
空間型のリテラル形式はありません。 ただし、Well-Known Text 形式の文字列を使用して呼び出す正規の Entity Framework 関数を使用できます。 たとえば、次の関数呼び出しでは、ジオメトリ ポイントが作成されます。  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions メソッド](http://msdn.microsoft.com/library/hh749531.aspx)ページには、空間に関する正規 Entity Framework メソッドすべてが一覧表示されます。 目的のメソッドをクリックすると、関数に渡す必要のあるパラメーターを確認できます。
