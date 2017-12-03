---
title: "Visual Studio 2010 での .NET Framework 3.0 および 3.5 を対象とするプロジェクトの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="5696c-102">Visual Studio 2010 での .NET Framework 3.0 および 3.5 を対象とするプロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="5696c-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="5696c-103">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を使用して、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Version 3.0 または 3.5 を対象とするプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5696c-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="5696c-104">このトピックでは、この実行方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5696c-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5696c-105">アクティビティを追加する際は、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の必要なバージョンが設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5696c-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="5696c-106">アクティビティを追加した後でワークフローのターゲット バージョンを変更すると、ワークフロー検証が失敗します。</span><span class="sxs-lookup"><span data-stu-id="5696c-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5696c-107">.Net Framework 3.5 アクティビティを持つ [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] で既存のワークフローを開くと、`this.SetValue()` でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5696c-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="5696c-108">以前のバージョンの .Net Framework で作成されたプロジェクトを開くには、最初にデザイナーで空白のワークフローを開き、.Net Framework 3.5 アクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="5696c-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="5696c-109">Visual Studio 2010 で .NET Framework 3.0 または 3.5 プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="5696c-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="5696c-110">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="5696c-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5696c-111">選択**ファイル**、**新しい**、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="5696c-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="5696c-112">ダイアログ ボックス最上部のボックスで、必要なバージョンの [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5696c-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="5696c-113">対象となる .NET Framework のバージョンをアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="5696c-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="5696c-114">ソリューション エクスプ ローラーでプロジェクトを右クリックし **プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="5696c-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="5696c-115">**ターゲット フレームワーク**ドロップダウン リストで、目的のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="5696c-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
