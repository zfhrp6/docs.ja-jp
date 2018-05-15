---
title: クエリにおける注釈の使用
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 692bc965fb62996c205d4e3d1061d8483a4f652c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="4c3bf-102">クエリにおける注釈の使用</span><span class="sxs-lookup"><span data-stu-id="4c3bf-102">Using Annotation in Queries</span></span>
<span data-ttu-id="4c3bf-103">注釈を使用すると、ビルド後に構成できる値を使用して、追跡レコードへのタグ付けを任意に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4c3bf-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="4c3bf-104">たとえば、"Mail Server"とタグ付けを複数のワークフローの複数の追跡レコード場合もあります = ="Mail server1"というです。</span><span class="sxs-lookup"><span data-stu-id="4c3bf-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="4c3bf-105">こうすると、後で追跡レコードのクエリを実行するときに、このタグの付いたすべてのレコードを簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="4c3bf-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="4c3bf-106">注釈の追加</span><span class="sxs-lookup"><span data-stu-id="4c3bf-106">Adding Annotations</span></span>  
 <span data-ttu-id="4c3bf-107">次の例に示すように、追跡クエリに注釈を追加できます。</span><span class="sxs-lookup"><span data-stu-id="4c3bf-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
>  <span data-ttu-id="4c3bf-108">これらの追跡クエリ要素は、追跡プロファイルの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c3bf-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="4c3bf-109">追跡プロファイルは構成またはコードで作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c3bf-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c3bf-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c3bf-110">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="4c3bf-111">\<participants></span><span class="sxs-lookup"><span data-stu-id="4c3bf-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [<span data-ttu-id="4c3bf-112">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="4c3bf-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4c3bf-113">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="4c3bf-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
