---
title: "方法 : Windows フォームに ActiveX コントロールを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 940dd21fc48c23ce623280aab2c487db5810057c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="24db1-102">方法 : Windows フォームに ActiveX コントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="24db1-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="24db1-103">Windows フォーム コントロールをホストするには、Windows フォーム デザイナーが最適化され、ときにも Windows フォームで ActiveX コントロールを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="24db1-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="24db1-104">ActiveX コントロールに追加されるときに、Windows フォームのパフォーマンスの制限があります。</span><span class="sxs-lookup"><span data-stu-id="24db1-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="24db1-105">ActiveX コントロールをフォームに追加する前に、ツールボックスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24db1-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="24db1-106">詳細については、次を参照してください。 [COM コンポーネント、ツールボックスのカスタマイズ ダイアログ ボックス](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c)です。</span><span class="sxs-lookup"><span data-stu-id="24db1-106">For more information, see [COM Components, Customize Toolbox Dialog Box](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24db1-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24db1-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="24db1-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24db1-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="24db1-109">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24db1-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="24db1-110">Windows フォームに ActiveX コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="24db1-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="24db1-111">ツールボックスでコントロールをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="24db1-111">Double-click the control on the Toolbox.</span></span>  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="24db1-112">プロジェクトのコントロールへのすべての参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="24db1-112"> adds all references to the control in your project.</span></span> <span data-ttu-id="24db1-113">Windows フォームで ActiveX コントロールを使用する場合に留意すべきことに関する詳細については、次を参照してください。 [Windows フォームで ActiveX コントロールをホストしている場合の考慮事項](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)です。</span><span class="sxs-lookup"><span data-stu-id="24db1-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="24db1-114">Windows フォーム ActiveX コントロール インポーター (AxImp.exe) は、ActiveX のダイナミック リンク ライブラリのインポート時に予想よりも、別の種類のイベント引数を作成します。</span><span class="sxs-lookup"><span data-stu-id="24db1-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="24db1-115">AxImp.exe によって作成された引数は、次のような: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`、`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`が必要です。</span><span class="sxs-lookup"><span data-stu-id="24db1-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="24db1-116">この不規則性は防止しませんコードが正常に注意してください。</span><span class="sxs-lookup"><span data-stu-id="24db1-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="24db1-117">詳細については、「 [Windows フォーム ActiveX コントロール インポーター (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)です。</span><span class="sxs-lookup"><span data-stu-id="24db1-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24db1-118">参照</span><span class="sxs-lookup"><span data-stu-id="24db1-118">See Also</span></span>  
 [<span data-ttu-id="24db1-119">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="24db1-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="24db1-120">各言語およびライブラリにおける、コントロールとプログラミング可能オブジェクトの比較</span><span class="sxs-lookup"><span data-stu-id="24db1-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="24db1-121">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="24db1-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="24db1-122">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="24db1-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="24db1-123">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="24db1-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="24db1-124">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="24db1-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="24db1-125">Windows フォーム コントロールの機能別一覧</span><span class="sxs-lookup"><span data-stu-id="24db1-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
