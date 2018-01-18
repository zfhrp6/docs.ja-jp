---
title: "挿入、更新、および削除の各操作のカスタマイズ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa12b26723c3c97e45f75ae951a7496025fde5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="6e665-102">挿入、更新、および削除の各操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="6e665-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="6e665-103">既定で、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、挿入、読み取り、更新、および削除の各操作を実装する動的な SQL を生成します。</span><span class="sxs-lookup"><span data-stu-id="6e665-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="6e665-104">ただし、実際の使用では、業務ニーズに合わせてアプリケーションをカスタマイズすることが多くなります。</span><span class="sxs-lookup"><span data-stu-id="6e665-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e665-105">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] を使って挿入、更新、および削除の各操作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="6e665-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="6e665-106">ここでは、挿入、読み取り、更新、および削除の各操作をアプリケーションでカスタマイズするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に用意されている手段について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e665-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e665-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6e665-107">In This Section</span></span>  
 [<span data-ttu-id="6e665-108">操作のカスタマイズの概要</span><span class="sxs-lookup"><span data-stu-id="6e665-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="6e665-109">挿入、読み取り、更新、および削除の各操作をカスタマイズするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に用意されている手段について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e665-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="6e665-110">挿入、更新、および削除の各操作</span><span class="sxs-lookup"><span data-stu-id="6e665-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="6e665-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の既定のデータベース データ操作手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e665-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="6e665-112">既定の動作をオーバーライドするときの開発者の責任</span><span class="sxs-lookup"><span data-stu-id="6e665-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="6e665-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって強制されない要件を実装するときの開発者の役割について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e665-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="6e665-114">部分メソッドによるビジネス ロジックの追加</span><span class="sxs-lookup"><span data-stu-id="6e665-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="6e665-115">自動生成されるメソッドをオーバーライドするために部分メソッドを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e665-115">Describes how to use partial methods to override autogenerated methods.</span></span>
