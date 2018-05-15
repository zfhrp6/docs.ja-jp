---
title: カスタム追跡レコード
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 6c68c08e5beacee30b517bf0c2bad3e83785409b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="custom-tracking-records"></a><span data-ttu-id="e8a92-102">カスタム追跡レコード</span><span class="sxs-lookup"><span data-stu-id="e8a92-102">Custom Tracking Records</span></span>
<span data-ttu-id="e8a92-103">このトピックではカスタム追跡レコードを作成し、出力されたデータをレコードと一緒に読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e8a92-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="e8a92-104">カスタム追跡レコードの出力</span><span class="sxs-lookup"><span data-stu-id="e8a92-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="e8a92-105">次の例に示すように、カスタム追跡レコードはコード アクティビティから出力できます。</span><span class="sxs-lookup"><span data-stu-id="e8a92-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="e8a92-106"><xref:System.Activities.Tracking.CustomTrackingRecord> 上で <xref:System.Activities.NativeActivityContext.Track%2A> メソッドを呼び出すことで、`ActvityContext` をコード アクティビティに出力できます。</span><span class="sxs-lookup"><span data-stu-id="e8a92-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a92-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8a92-107">See Also</span></span>  
 [<span data-ttu-id="e8a92-108">Windows Server App Fabric の監視</span><span class="sxs-lookup"><span data-stu-id="e8a92-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="e8a92-109">アプリケーション App Fabric の監視</span><span class="sxs-lookup"><span data-stu-id="e8a92-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
