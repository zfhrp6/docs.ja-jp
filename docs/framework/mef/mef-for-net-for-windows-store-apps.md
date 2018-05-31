---
title: Windows ストア アプリ用 .NET 用 MEF
ms.date: 03/30/2017
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26c2c6cd701f15ca950d399cf3074ee229534d65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388860"
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="a90cf-102">Windows ストア アプリ用 .NET 用 MEF</span><span class="sxs-lookup"><span data-stu-id="a90cf-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="a90cf-103"><xref:System.Composition?displayProperty=nameWithType> とその子名前空間には、Managed Extensibility Framework (MEF) を使用して拡張可能な [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリを開発するための型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a90cf-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="a90cf-104">これらの名前空間は、[!INCLUDE[win8](../../../includes/win8-md.md)] オペレーティング システムの [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] サブセットの一部です。</span><span class="sxs-lookup"><span data-stu-id="a90cf-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="a90cf-105">これらの名前空間は、.NET Framework で配布されているコア クラス ライブラリの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="a90cf-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="a90cf-106">これらの名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、**[プロジェクト]** メニューの **[Manage NuGet Packages]** をクリックし、Microsoft.Composition パッケージをオンライン検索します。</span><span class="sxs-lookup"><span data-stu-id="a90cf-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="a90cf-107"><xref:System.Composition?displayProperty=nameWithType> は、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリのコア MEF を構成するクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a90cf-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="a90cf-108"><xref:System.Composition.Convention?displayProperty=nameWithType> は、規則に基づく構成モデルでの MEF の使用をサポートする型を提供します。</span><span class="sxs-lookup"><span data-stu-id="a90cf-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="a90cf-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> は、ホスト アプリケーションの開発者に役立つ MEF 型を提供します。</span><span class="sxs-lookup"><span data-stu-id="a90cf-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="a90cf-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> は、合成エンジンによって内部的に使用される MEF 型を提供します。</span><span class="sxs-lookup"><span data-stu-id="a90cf-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="a90cf-111">[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] についての詳細およびそれに含まれる名前空間と型の一覧については、Windows デベロッパー センターで「[Windows ストア アプリ用 .NET の概要](http://go.microsoft.com/fwlink/p/?LinkID=238312)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a90cf-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90cf-112">参照</span><span class="sxs-lookup"><span data-stu-id="a90cf-112">See Also</span></span>  
 [<span data-ttu-id="a90cf-113">Windows ストア アプリ用 .NET の概要</span><span class="sxs-lookup"><span data-stu-id="a90cf-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="a90cf-114">Windows ストア アプリ用 .NET – サポートされている API</span><span class="sxs-lookup"><span data-stu-id="a90cf-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="a90cf-115">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="a90cf-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
