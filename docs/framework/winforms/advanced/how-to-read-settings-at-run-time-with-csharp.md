---
title: "方法 : 実行時に設定を C# で読み取る"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85dc3a2c97b8fe5003c6026874dbdcaa9af89d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="cd92e-102">方法 : 実行時に設定を C# で読み取る</span><span class="sxs-lookup"><span data-stu-id="cd92e-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="cd92e-103">アプリケーション スコープの設定とユーザー スコープの設定は、どちらも実行時に Properties オブジェクトを使用して読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="cd92e-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="cd92e-104">Properties オブジェクトは、プロジェクトのすべての既定の設定を、Properties.Settings.Default メンバーを介して公開します。</span><span class="sxs-lookup"><span data-stu-id="cd92e-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="cd92e-105">実行時に設定を C# で読み取るには</span><span class="sxs-lookup"><span data-stu-id="cd92e-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="cd92e-106">Properties.Settings.Default メンバーを介して適切な設定にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cd92e-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="cd92e-107">BackColor プロパティに `myColor` という名前の設定を割り当てる方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cd92e-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="cd92e-108">この例を実行する前に、`myColor` という名前の `System.Drawing.Color` 型の設定を含む設定ファイルを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd92e-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="cd92e-109">設定ファイルを作成する方法の詳細については、次を参照してください。[操作方法: デザイン時に新しい設定の作成](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd92e-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cd92e-110">参照</span><span class="sxs-lookup"><span data-stu-id="cd92e-110">See Also</span></span>  
 [<span data-ttu-id="cd92e-111">アプリケーション設定とユーザー設定の使用</span><span class="sxs-lookup"><span data-stu-id="cd92e-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="cd92e-112">方法: 実行時にユーザー設定を C# で書き込む</span><span class="sxs-lookup"><span data-stu-id="cd92e-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="cd92e-113">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="cd92e-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
