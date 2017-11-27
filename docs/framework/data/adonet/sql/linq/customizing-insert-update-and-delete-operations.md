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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e48ac307087d5b90567c720d0c215ac0d52ccb6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="d553f-102">挿入、更新、および削除の各操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="d553f-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="d553f-103">既定で、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、挿入、読み取り、更新、および削除の各操作を実装する動的な SQL を生成します。</span><span class="sxs-lookup"><span data-stu-id="d553f-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="d553f-104">ただし、実際の使用では、業務ニーズに合わせてアプリケーションをカスタマイズすることが多くなります。</span><span class="sxs-lookup"><span data-stu-id="d553f-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d553f-105">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] を使って挿入、更新、および削除の各操作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d553f-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="d553f-106">ここでは、挿入、読み取り、更新、および削除の各操作をアプリケーションでカスタマイズするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に用意されている手段について説明します。</span><span class="sxs-lookup"><span data-stu-id="d553f-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d553f-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d553f-107">In This Section</span></span>  
 [<span data-ttu-id="d553f-108">操作のカスタマイズ: 概要</span><span class="sxs-lookup"><span data-stu-id="d553f-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="d553f-109">挿入、読み取り、更新、および削除の各操作をカスタマイズするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に用意されている手段について説明します。</span><span class="sxs-lookup"><span data-stu-id="d553f-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="d553f-110">Insert、Update、および削除操作</span><span class="sxs-lookup"><span data-stu-id="d553f-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="d553f-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の既定のデータベース データ操作手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d553f-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="d553f-112">既定の動作をオーバーライドするときの開発者の責任</span><span class="sxs-lookup"><span data-stu-id="d553f-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="d553f-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって強制されない要件を実装するときの開発者の役割について説明します。</span><span class="sxs-lookup"><span data-stu-id="d553f-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="d553f-114">部分メソッドを使用してビジネス ロジックを追加します。</span><span class="sxs-lookup"><span data-stu-id="d553f-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="d553f-115">自動生成されるメソッドをオーバーライドするために部分メソッドを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d553f-115">Describes how to use partial methods to override autogenerated methods.</span></span>
