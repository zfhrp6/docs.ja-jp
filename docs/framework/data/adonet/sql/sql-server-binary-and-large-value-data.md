---
title: SQL Server のバイナリ データと大きな値のデータ
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: c0202f6dc17d36fafb28206e17b71fc6d68d88c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363407"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="8dd2d-102">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="8dd2d-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="8dd2d-103">SQL Server では `max` 指定子が提供されています。これにより、`varchar`、`nvarchar`、および `varbinary` データ型の記憶容量が拡張されています。</span><span class="sxs-lookup"><span data-stu-id="8dd2d-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="8dd2d-104">`varchar(max)`、 `nvarchar(max)`、および`varbinary(max)`総称して*大きな値データ型*です。</span><span class="sxs-lookup"><span data-stu-id="8dd2d-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="8dd2d-105">大きな値のデータ型を使用すると、最大で 2^31-1 バイトのデータを格納できます。</span><span class="sxs-lookup"><span data-stu-id="8dd2d-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="8dd2d-106">SQL Server 2008 では FILESTREAM 属性が導入されました。これはデータ型ではありませんが、列に定義できる属性であり、これを使用すると大きな値のデータをデータベースではなくファイル システムに格納できます。</span><span class="sxs-lookup"><span data-stu-id="8dd2d-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8dd2d-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8dd2d-107">In This Section</span></span>  
 [<span data-ttu-id="8dd2d-108">ADO.NET での大きい値 (max) データの変更</span><span class="sxs-lookup"><span data-stu-id="8dd2d-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="8dd2d-109">大きな値のデータ型を扱う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dd2d-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="8dd2d-110">FILESTREAM データ</span><span class="sxs-lookup"><span data-stu-id="8dd2d-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="8dd2d-111">SQL Server 2008 で FILESTREAM 属性を使用して保存された大きな値のデータを扱う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dd2d-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd2d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8dd2d-112">See Also</span></span>  
 [<span data-ttu-id="8dd2d-113">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8dd2d-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="8dd2d-114">ADO.NET における SQL Server データ操作</span><span class="sxs-lookup"><span data-stu-id="8dd2d-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="8dd2d-115">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="8dd2d-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="8dd2d-116">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="8dd2d-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
