---
title: "セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 461bc36fd85a158e67c29c3f4ad001997218c824
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security"></a><span data-ttu-id="4806e-102">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4806e-102">Security</span></span>
<span data-ttu-id="4806e-103">SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。</span><span class="sxs-lookup"><span data-stu-id="4806e-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="4806e-104">**System.Activities.DurableInstancing.InstanceStoreUsers**です。</span><span class="sxs-lookup"><span data-stu-id="4806e-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="4806e-105">このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。</span><span class="sxs-lookup"><span data-stu-id="4806e-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="4806e-106">**System.Activities.DurableInstancing.InstanceStoreObservers**です。</span><span class="sxs-lookup"><span data-stu-id="4806e-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="4806e-107">このロールには、パブリック ビューへの読み取り専用アクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="4806e-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="4806e-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**です。</span><span class="sxs-lookup"><span data-stu-id="4806e-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="4806e-109">このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。</span><span class="sxs-lookup"><span data-stu-id="4806e-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="4806e-110">インスタンスのアクティブ化の詳細については、次を参照してください。[インスタンスのアクティブ化](../../../docs/framework/windows-workflow-foundation/instance-activation.md)です。</span><span class="sxs-lookup"><span data-stu-id="4806e-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="4806e-111">汎用ホスト ([!INCLUDE[dublin](../../../includes/dublin-md.md)] のワークフロー管理サービスなど) を実行するユーザー アカウントは、このデータベース ロールに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4806e-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4806e-112">Windows Server App Fabric で永続化ストアのセキュリティを参照してください[App Fabric で永続的ストアに対するセキュリティの構成](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="4806e-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4806e-113">インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4806e-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="4806e-114">インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="4806e-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="4806e-115">個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。</span><span class="sxs-lookup"><span data-stu-id="4806e-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
