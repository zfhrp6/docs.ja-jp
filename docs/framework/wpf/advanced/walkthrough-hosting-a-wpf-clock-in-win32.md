---
title: "チュートリアル: Win32 での WPF クロックのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caf652f8a80da8e927a74ffc012d09b2389b1b09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="1a3a2-102">チュートリアル: Win32 での WPF クロックのホスト</span><span class="sxs-lookup"><span data-stu-id="1a3a2-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>
<span data-ttu-id="1a3a2-103">配置する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーションに、<xref:System.Windows.Interop.HwndSource>を含む HWND を提供する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="1a3a2-104">最初に作成、 <xref:System.Windows.Interop.HwndSource>CreateWindow のようなパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span>  <span data-ttu-id="1a3a2-105">指示、<xref:System.Windows.Interop.HwndSource>に関する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内部するコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span>  <span data-ttu-id="1a3a2-106">最後に、HWND のうち、<xref:System.Windows.Interop.HwndSource>です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="1a3a2-107">このチュートリアルは、混合を作成する方法を示しています。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]オペレーティング システムを reimplements アプリケーション**日付と時刻のプロパティ**ダイアログ。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1a3a2-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1a3a2-108">Prerequisites</span></span>  
 <span data-ttu-id="1a3a2-109">参照してください[WPF および Win32 の相互運用](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-109">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="1a3a2-110">このチュートリアルを使用する方法</span><span class="sxs-lookup"><span data-stu-id="1a3a2-110">How to Use This Tutorial</span></span>  
 <span data-ttu-id="1a3a2-111">このチュートリアルの相互運用アプリケーションを生成する重要な手順に重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="1a3a2-112">サンプルは、このチュートリアルに基づく[クロックの相互運用の Win32 サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)が、そのサンプルは、最終的な製品の反射です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="1a3a2-113">既存の開始された場合、このチュートリアル手順について説明[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]独自のプロジェクト、おそらく、既存のプロジェクトを追加して仮定ホストされた[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="1a3a2-114">最終的な製品を比較する[クロックの相互運用の Win32 サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-114">You can compare your end product with [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="1a3a2-115">Windows Presentation Framework Win32 内のチュートリアル (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="1a3a2-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>  
 <span data-ttu-id="1a3a2-116">次の図は、このチュートリアルの目的の最終製品を示しています。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-116">The following graphic shows the intended end product of this tutorial:</span></span>  
  
 <span data-ttu-id="1a3a2-117">![日付と時刻のプロパティ ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span><span class="sxs-lookup"><span data-stu-id="1a3a2-117">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span></span>  
  
 <span data-ttu-id="1a3a2-118">C++ を作成することでこのダイアログ ボックスを作成し直すことができます[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクト[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、ダイアログ エディターを使用して、次を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-118">You can recreate this dialog by creating C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and using the dialog editor to create the following:</span></span>  
  
 <span data-ttu-id="1a3a2-119">![日付と時刻のプロパティ ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span><span class="sxs-lookup"><span data-stu-id="1a3a2-119">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span></span>  
  
 <span data-ttu-id="1a3a2-120">(を使用する必要はありません[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]を使用する<xref:System.Windows.Interop.HwndSource>、書き込みに C++ を使用する必要はありませんし[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]をそれを行うには非常に典型的な方法は、プログラムが、このステップワイズのチュートリアルについてにも適しています)。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>  
  
 <span data-ttu-id="1a3a2-121">配置するために特定の 5 つの手順を実行する必要があります、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ダイアログ ボックスにクロック。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>  
  
1.  <span data-ttu-id="1a3a2-122">有効にする、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]マネージ コードを呼び出すためのプロジェクト (**/clr**) のプロジェクト設定を変更することによって[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="1a3a2-123">作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>別個の DLL にします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>  
  
3.  <span data-ttu-id="1a3a2-124">追加すること[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>内、<xref:System.Windows.Interop.HwndSource>です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>  
  
4.  <span data-ttu-id="1a3a2-125">そのため、HWND を取得<xref:System.Windows.Controls.Page>を使用して、<xref:System.Windows.Interop.HwndSource.Handle%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>  
  
5.  <span data-ttu-id="1a3a2-126">使用して[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]内で、大きい方の HWND を配置する場所を決定する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーション</span><span class="sxs-lookup"><span data-stu-id="1a3a2-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>  
  
## <a name="clr"></a><span data-ttu-id="1a3a2-127">/clr</span><span class="sxs-lookup"><span data-stu-id="1a3a2-127">/clr</span></span>  
 <span data-ttu-id="1a3a2-128">アンマネージこれを有効にするのには、まず[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]マネージ コードをプロジェクトに呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span>  <span data-ttu-id="1a3a2-129">/Clr コンパイラ オプションを使用して、使用するため、Main メソッドを調整するために必要な Dll にリンクを使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="1a3a2-130">C++ プロジェクト内でマネージ コードの使用を有効にする: win32clock プロジェクトを右クリックし **プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span>  <span data-ttu-id="1a3a2-131">**全般**プロパティ ページ (既定)、変更を共通言語ランタイム サポート`/clr`です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>  
  
 <span data-ttu-id="1a3a2-132">次に、ために必要な Dll への参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll、PresentationFramework.dll、System.dll、WindowsBase.dll、UIAutomationProvider.dll および UIAutomationTypes.dll です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="1a3a2-133">(次の手順と c: ドライブにオペレーティング システムをインストールします。)</span><span class="sxs-lookup"><span data-stu-id="1a3a2-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>  
  
1.  <span data-ttu-id="1a3a2-134">Win32clock プロジェクトを右クリックし **参照しています.**、そのダイアログ ボックス内。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>  
  
2.  <span data-ttu-id="1a3a2-135">Win32clock プロジェクトを右クリックし **参照しています.**.</span><span class="sxs-lookup"><span data-stu-id="1a3a2-135">Right-click win32clock project and select **References...**.</span></span>  
  
3.  <span data-ttu-id="1a3a2-136">をクリックして**新しい参照の追加**[参照] タブをクリックして、C:\Program \reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll を入力して [ok] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>  
  
4.  <span data-ttu-id="1a3a2-137">PresentationFramework.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>  
  
5.  <span data-ttu-id="1a3a2-138">WindowsBase.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>  
  
6.  <span data-ttu-id="1a3a2-139">UIAutomationTypes.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>  
  
7.  <span data-ttu-id="1a3a2-140">UIAutomationProvider.dll に対して操作を繰り返します。 C:\Program \reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>  
  
8.  <span data-ttu-id="1a3a2-141">をクリックして**新しい参照の追加**System.dll を選択して、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>  
  
9. <span data-ttu-id="1a3a2-142">をクリックして**OK**参照の追加の win32clock プロパティ ページを終了します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
 <span data-ttu-id="1a3a2-143">最後に、追加、`STAThreadAttribute`を`_tWinMain`で使用するためのメソッド[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1a3a2-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 <span data-ttu-id="1a3a2-144">この属性は、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]の初期化時[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]、シングル スレッド アパートメント (STA) はあるモデルに必要なを使用する必要があります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>  
  
## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="1a3a2-145">Windows Presentation Framework ページを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-145">Create a Windows Presentation Framework Page</span></span>  
 <span data-ttu-id="1a3a2-146">次に、定義する DLL を作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1a3a2-147">作成する最も簡単なは多くの場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>スタンドアロン アプリケーションでは、書き込みとデバッグ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分ようにします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span>  <span data-ttu-id="1a3a2-148">クリックすると、プロジェクトを右クリックして、DLL にそのプロジェクトを変換できますが終わったら、**プロパティ**しようとして、アプリケーション、および Windows クラス ライブラリに出力の種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>  
  
 <span data-ttu-id="1a3a2-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll プロジェクト、組み合わせて使用できる、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 、ソリューションを右クリックしてプロジェクト (1 つのソリューションを 2 つのプロジェクトを含む) – **Add\Existing プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>  
  
 <span data-ttu-id="1a3a2-150">使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から dll、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクト参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>  
  
1.  <span data-ttu-id="1a3a2-151">Win32clock プロジェクトを右クリックし **参照しています.**.</span><span class="sxs-lookup"><span data-stu-id="1a3a2-151">Right-click win32clock project and select **References...**.</span></span>  
  
2.  <span data-ttu-id="1a3a2-152">をクリックして**新しい参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-152">Click **Add New Reference**.</span></span>  
  
3.  <span data-ttu-id="1a3a2-153">**[プロジェクト]** タブをクリックします。WPFClock を選択し、[ok] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-153">Click the **Projects** tab.  Select WPFClock, click OK.</span></span>  
  
4.  <span data-ttu-id="1a3a2-154">をクリックして**OK**参照の追加の win32clock プロパティ ページを終了します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
## <a name="hwndsource"></a><span data-ttu-id="1a3a2-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="1a3a2-155">HwndSource</span></span>  
 <span data-ttu-id="1a3a2-156">次に、<xref:System.Windows.Interop.HwndSource>させる、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND のようになります。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span>  <span data-ttu-id="1a3a2-157">C++ ファイルには、コードのブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-157">You add this block of code to a C++ file:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
  
    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
        HwndSource^ source = gcnew HwndSource(  
            0, // class style  
            WS_VISIBLE | WS_CHILD, // style  
            0, // exstyle  
            x, y, width, height,  
            "hi", // NAME  
            IntPtr(parent)        // parent window   
            );  
  
        UIElement^ page = gcnew WPFClock::Clock();  
        source->RootVisual = page;  
        return (HWND) source->Handle.ToPointer();  
    }  
}  
}  
```  
  
 <span data-ttu-id="1a3a2-158">これは、いくつかの説明が使用できるコードの長いです。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-158">This is a long piece of code that could use some explanation.</span></span>  <span data-ttu-id="1a3a2-159">最初の部分がさまざまな句すべての呼び出しを完全に修飾する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 <span data-ttu-id="1a3a2-160">作成する関数を定義し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、配置、<xref:System.Windows.Interop.HwndSource>周囲、および、HWND を返します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 <span data-ttu-id="1a3a2-161">最初に作成、<xref:System.Windows.Interop.HwndSource>パラメーターを持つは CreateWindow に似ています。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 <span data-ttu-id="1a3a2-162">作成してから、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラスをコンス トラクターを呼び出してコンテンツします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 <span data-ttu-id="1a3a2-163">ページを接続する、 <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="1a3a2-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
source->RootVisual = page;  
```  
  
 <span data-ttu-id="1a3a2-164">最後の行で、HWND を返すと、 <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="1a3a2-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a><span data-ttu-id="1a3a2-165">Hwnd を配置</span><span class="sxs-lookup"><span data-stu-id="1a3a2-165">Positioning the Hwnd</span></span>  
 <span data-ttu-id="1a3a2-166">含む HWND をしたら、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計の内部には、その HWND を配置する必要があります、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ダイアログ。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span>  <span data-ttu-id="1a3a2-167">そのサイズと場所を渡す場合だけ、HWND を配置する場所がわかっている場合、`GetHwnd`前に定義した関数です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span>  <span data-ttu-id="1a3a2-168">正確に一致しないことを確認して、Hwnd のいずれかが配置されているので、ダイアログ ボックスの定義にリソース ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span>  <span data-ttu-id="1a3a2-169">使用することができます、[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]にダイアログ エディター、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]スタティック コントロールにクロックを移動する (「挿入クロックここで」)、配置に使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロック。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>  
  
 <span data-ttu-id="1a3a2-170">WM_INITDIALOG を処理する場所を使用する`GetDlgItem`を静的なプレース ホルダーの HWND を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 <span data-ttu-id="1a3a2-171">計算するサイズと位置の静的なプレース ホルダーを配置できるように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]その場所にクロックします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>  
  
 <span data-ttu-id="1a3a2-172">RECT 四角形です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-172">RECT rectangle;</span></span>  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 <span data-ttu-id="1a3a2-173">非表示にするプレース ホルダーの静的。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-173">Then you hide the placeholder STATIC:</span></span>  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 <span data-ttu-id="1a3a2-174">作成し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計の HWND をその場所に。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 <span data-ttu-id="1a3a2-175">実行するチュートリアル興味深いし、実数を生成するために[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計を作成する必要が、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールをこの時点でクロックします。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="1a3a2-176">分離コード内のいくつかのイベント ハンドラーを持つため、マークアップで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="1a3a2-177">このチュートリアルは、相互運用の概要とコントロールのデザインに関するされませんが後のコードを完了、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロックが提供されるを構築または各部の意味については不連続指示せず、コード ブロックを図って、ここです。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="1a3a2-178">自由ルック アンド フィールまたはコントロールの機能を変更するには、このコードをお試しください。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>  
  
 <span data-ttu-id="1a3a2-179">マークアップを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-179">Here is the markup:</span></span>  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 <span data-ttu-id="1a3a2-180">付随する分離コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-180">And here is the accompanying code-behind:</span></span>  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 <span data-ttu-id="1a3a2-181">最終的な結果は、ようになります。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-181">The final result looks like:</span></span>  
  
 <span data-ttu-id="1a3a2-182">![日付と時刻のプロパティ ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span><span class="sxs-lookup"><span data-stu-id="1a3a2-182">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span></span>  
  
 <span data-ttu-id="1a3a2-183">このスクリーン ショットを作成したコードに、最終結果を比較するを参照してください。[クロックの相互運用の Win32 サンプル](http://go.microsoft.com/fwlink/?LinkID=160051)です。</span><span class="sxs-lookup"><span data-stu-id="1a3a2-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3a2-184">参照</span><span class="sxs-lookup"><span data-stu-id="1a3a2-184">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="1a3a2-185">WPF と Win32 の相互運用性</span><span class="sxs-lookup"><span data-stu-id="1a3a2-185">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [<span data-ttu-id="1a3a2-186">Win32 クロックの相互運用性サンプル</span><span class="sxs-lookup"><span data-stu-id="1a3a2-186">Win32 Clock Interoperation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160051)
