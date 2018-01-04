---
title: "方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1323ffbd59a14d19d1161e0718fad083bcc37a89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="d8566-102">方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する</span><span class="sxs-lookup"><span data-stu-id="d8566-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="d8566-103">を作成およびコントロールを配置することがそれらのコントロールに表示される、**ツールボックス アイテムの選択**を右クリックしたときに表示されるダイアログ ボックスで、**ツールボックス**選択**項目を選択して**です。</span><span class="sxs-lookup"><span data-stu-id="d8566-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="d8566-104">AssemblyFoldersEx 登録手順を使用してこのダイアログ ボックスに表示するコントロールを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d8566-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="d8566-105">ツールボックス アイテムの選択 ダイアログ ボックスで、コントロールを表示するには</span><span class="sxs-lookup"><span data-stu-id="d8566-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="d8566-106">コントロール アセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="d8566-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="d8566-107">詳細については、次を参照してください[する方法: グローバル アセンブリ キャッシュにアセンブリをインストール。](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="d8566-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="d8566-108">- または -</span><span class="sxs-lookup"><span data-stu-id="d8566-108">-or-</span></span>  
  
-   <span data-ttu-id="d8566-109">AssemblyFoldersEx 登録手順を使用して、コントロールとその関連付けられたデザイン時アセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="d8566-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="d8566-110">AssemblyFoldersEx は、サード パーティ ベンダーがサポートされる framework の各バージョンのパスを格納する場所のレジストリの場所です。</span><span class="sxs-lookup"><span data-stu-id="d8566-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="d8566-111">デザイン時の解像度は、この参照アセンブリを検索するレジストリの場所で確認できます。</span><span class="sxs-lookup"><span data-stu-id="d8566-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="d8566-112">レジストリ スクリプトは、ツールボックスに表示するコントロールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d8566-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="d8566-113">詳細については、次を参照してください。[カスタム コントロールとデザイン時アセンブリ (Visual Studio 2013) の展開](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)です。</span><span class="sxs-lookup"><span data-stu-id="d8566-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8566-114">参照</span><span class="sxs-lookup"><span data-stu-id="d8566-114">See Also</span></span>  
 <span data-ttu-id="d8566-115">[[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)</span><span class="sxs-lookup"><span data-stu-id="d8566-115">[Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)</span></span>  
 [<span data-ttu-id="d8566-116">カスタム コントロールとデザイン時アセンブリ (Visual Studio 2013) の展開</span><span class="sxs-lookup"><span data-stu-id="d8566-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="d8566-117">デザイン時の Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="d8566-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="d8566-118">方法: グローバル アセンブリ キャッシュにアセンブリをインストールする</span><span class="sxs-lookup"><span data-stu-id="d8566-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="d8566-119">チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定</span><span class="sxs-lookup"><span data-stu-id="d8566-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
