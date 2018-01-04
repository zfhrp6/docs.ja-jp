---
title: "方法 : アプリケーション セッション間で設定値を変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c00e61001d9c8877b1fcaa0e938c92249c7915e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="33f78-102">方法 : アプリケーション セッション間で設定値を変更する</span><span class="sxs-lookup"><span data-stu-id="33f78-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="33f78-103">ときに、アプリケーションをコンパイルして、展開後に、アプリケーション セッション間での設定の値を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="33f78-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="33f78-104">たとえば、適切なデータベースの場所を指す接続文字列を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="33f78-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="33f78-105">アプリケーションをコンパイルして、展開後にデザイン時ツールが使用できないために、ファイルに手動で設定値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33f78-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="33f78-106">アプリケーション セッション間での設定の値を変更するには</span><span class="sxs-lookup"><span data-stu-id="33f78-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="33f78-107">メモ帳または他のテキストまたは XML エディターを使用して、アプリケーションを使用して関連する .config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="33f78-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="33f78-108">変更する設定のエントリを探します。</span><span class="sxs-lookup"><span data-stu-id="33f78-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="33f78-109">次に示す例のようになります。</span><span class="sxs-lookup"><span data-stu-id="33f78-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="33f78-110">設定の新しい値を入力し、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="33f78-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f78-111">参照</span><span class="sxs-lookup"><span data-stu-id="33f78-111">See Also</span></span>  
 [<span data-ttu-id="33f78-112">アプリケーション設定とユーザー設定の使用</span><span class="sxs-lookup"><span data-stu-id="33f78-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="33f78-113">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="33f78-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
