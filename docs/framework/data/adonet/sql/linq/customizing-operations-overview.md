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
ms.workload: dotnet
ms.openlocfilehash: 9776daa28b0a7ffcd3b721f004f5b9a44dd09f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="73c15-102">操作のカスタマイズの概要</span><span class="sxs-lookup"><span data-stu-id="73c15-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="73c15-103">既定では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、対応付けに基づいて、挿入、更新、および削除の各操作のための動的な SQL を生成します。</span><span class="sxs-lookup"><span data-stu-id="73c15-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="73c15-104">しかし実際には、セキュリティや検証などを目的とした独自のビジネス ロジックを追加することが必要になる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="73c15-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="73c15-105">これらの操作をカスタマイズするための手法には、次の項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="73c15-105"> techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="73c15-106">読み込みオプション</span><span class="sxs-lookup"><span data-stu-id="73c15-106">Loading Options</span></span>  
 <span data-ttu-id="73c15-107">クエリで、データベースに接続するときに、メイン ターゲットに関係するデータをどれだけ取得するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="73c15-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="73c15-108">この機能は主に、<xref:System.Data.Linq.DataLoadOptions> を使用して実装します。</span><span class="sxs-lookup"><span data-stu-id="73c15-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="73c15-109">詳細については、次を参照してください。[遅延実行と即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)です。</span><span class="sxs-lookup"><span data-stu-id="73c15-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="73c15-110">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="73c15-110">Partial Methods</span></span>  
 <span data-ttu-id="73c15-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による既定の対応付けでは、ビジネス ロジックの実装に使用できる部分メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="73c15-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="73c15-112">詳細については、次を参照してください。[を追加するビジネス ロジックでメソッドを使用して部分](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)です。</span><span class="sxs-lookup"><span data-stu-id="73c15-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="73c15-113">ストアド プロシージャおよびユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="73c15-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="73c15-114">ストアド プロシージャおよびユーザー定義関数の使用をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="73c15-114"> supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="73c15-115">ストアド プロシージャは、操作のカスタマイズによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="73c15-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="73c15-116">詳細については、「[ストアド プロシージャ](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73c15-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c15-117">参照</span><span class="sxs-lookup"><span data-stu-id="73c15-117">See Also</span></span>  
 [<span data-ttu-id="73c15-118">挿入、更新、および削除の各操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="73c15-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
