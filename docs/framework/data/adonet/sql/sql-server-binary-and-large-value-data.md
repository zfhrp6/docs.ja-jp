---
title: SQL Server のバイナリ データと大きな値のデータ
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: c0202f6dc17d36fafb28206e17b71fc6d68d88c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server のバイナリ データと大きな値のデータ
SQL Server では `max` 指定子が提供されています。これにより、`varchar`、`nvarchar`、および `varbinary` データ型の記憶容量が拡張されています。 `varchar(max)`、 `nvarchar(max)`、および`varbinary(max)`総称して*大きな値データ型*です。 大きな値のデータ型を使用すると、最大で 2^31-1 バイトのデータを格納できます。  
  
 SQL Server 2008 では FILESTREAM 属性が導入されました。これはデータ型ではありませんが、列に定義できる属性であり、これを使用すると大きな値のデータをデータベースではなくファイル システムに格納できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ADO.NET での大きい値 (max) データの変更](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 大きな値のデータ型を扱う方法について説明します。  
  
 [FILESTREAM データ](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 SQL Server 2008 で FILESTREAM 属性を使用して保存された大きな値のデータを扱う方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET における SQL Server データ操作](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
