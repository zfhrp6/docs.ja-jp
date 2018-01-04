---
title: "方法 : C# のアプリケーションに複数の設定セットを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d9bd7d0721aae8691fdbca4d7b934f820666536
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="ad67e-102">方法 : C# のアプリケーションに複数の設定セットを追加する</span><span class="sxs-lookup"><span data-stu-id="ad67e-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="ad67e-103">場合によってで、アプリケーションに複数セットの設定があることができます。</span><span class="sxs-lookup"><span data-stu-id="ad67e-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="ad67e-104">たとえばを開発しているアプリケーションの設定の特定のグループが頻繁に変更すると思われる場合だと考えられますファイルを置換できる、されるように 1 つのファイルに分離してその他の設定は変わりません。</span><span class="sxs-lookup"><span data-stu-id="ad67e-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="ad67e-105">Visual Studio では、複数のセットの設定をプロジェクトに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="ad67e-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="ad67e-106">設定の追加セットは、Properties.Settings オブジェクト経由でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ad67e-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="ad67e-107">アプリケーションに追加の設定セットを追加するには</span><span class="sxs-lookup"><span data-stu-id="ad67e-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="ad67e-108">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad67e-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="ad67e-109">**[新しい項目の追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="ad67e-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="ad67e-110">**新しい項目の追加**ダイアログ ボックスで、**設定ファイル**、ファイルの名前を入力して、をクリックして**追加**をソリューションに新しい設定ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="ad67e-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="ad67e-111">**ソリューション エクスプ ローラー**に、新しい設定ファイルをドラッグして、**プロパティ**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="ad67e-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="ad67e-112">これにより、コードで使用できる新しい設定です。</span><span class="sxs-lookup"><span data-stu-id="ad67e-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="ad67e-113">追加し、その他の設定ファイルと同様に、このファイルの設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad67e-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="ad67e-114">この設定は、Properties.Settings オブジェクトでのグループにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ad67e-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad67e-115">参照</span><span class="sxs-lookup"><span data-stu-id="ad67e-115">See Also</span></span>  
 [<span data-ttu-id="ad67e-116">アプリケーション設定とユーザー設定の使用</span><span class="sxs-lookup"><span data-stu-id="ad67e-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="ad67e-117">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="ad67e-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
