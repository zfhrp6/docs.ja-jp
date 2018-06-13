---
title: 空間関数
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7b78cbf4dc53ba1bc4148fa0077615e43cc8f9f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763931"
---
# <a name="spatial-functions"></a>空間関数
空間型のリテラル形式はありません。 ただし、Well-Known Text 形式の文字列を使用して呼び出す正規の Entity Framework 関数を使用できます。 たとえば、次の関数呼び出しでは、ジオメトリ ポイントが作成されます。  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions メソッド](http://msdn.microsoft.com/library/hh749531.aspx)ページには、空間に関する正規 Entity Framework メソッドすべてが一覧表示されます。 目的のメソッドをクリックすると、関数に渡す必要のあるパラメーターを確認できます。
