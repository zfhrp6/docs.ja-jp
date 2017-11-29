---
title: "Windows ストア アプリ用 .NET の MEF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f427656f9b385214db5b3bd26c4addb1122b35a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="b326f-102">Windows ストア アプリ用 .NET の MEF</span><span class="sxs-lookup"><span data-stu-id="b326f-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="b326f-103"><xref:System.Composition?displayProperty=nameWithType>その子名前空間は拡張可能な開発の種類を含める[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ Managed Extensibility Framework (MEF) にします。</span><span class="sxs-lookup"><span data-stu-id="b326f-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="b326f-104">これらの名前空間の一部である、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]のサブセット、[!INCLUDE[win8](../../../includes/win8-md.md)]オペレーティング システムです。</span><span class="sxs-lookup"><span data-stu-id="b326f-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="b326f-105">これらの名前空間は、.NET Framework で配布されているコア クラス ライブラリの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="b326f-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="b326f-106">これらの名前空間をインストールするでプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**から、**プロジェクト**] メニューの [し、Microsoft.Composition パッケージをオンライン検索します。</span><span class="sxs-lookup"><span data-stu-id="b326f-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="b326f-107"><xref:System.Composition?displayProperty=nameWithType>MEF の中核となるクラスを提供の[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ。</span><span class="sxs-lookup"><span data-stu-id="b326f-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="b326f-108"><xref:System.Composition.Convention?displayProperty=nameWithType>MEF を使用して、構成の規約に基づくモデルを含むをサポートする型を提供します。</span><span class="sxs-lookup"><span data-stu-id="b326f-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="b326f-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>ホスト アプリケーションの開発者に役立つ MEF 型を提供します。</span><span class="sxs-lookup"><span data-stu-id="b326f-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="b326f-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>合成エンジンによって内部的に使用される MEF 型を提供します。</span><span class="sxs-lookup"><span data-stu-id="b326f-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="b326f-111">詳細については[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]名前空間とそれに含まれる型の一覧を参照してください、 [.NET Windows ストア アプリの概要](http://go.microsoft.com/fwlink/p/?LinkID=238312)Windows デベロッパー センターにします。</span><span class="sxs-lookup"><span data-stu-id="b326f-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b326f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b326f-112">See Also</span></span>  
 [<span data-ttu-id="b326f-113">.NET Windows ストア アプリの概要</span><span class="sxs-lookup"><span data-stu-id="b326f-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="b326f-114">Windows ストア アプリ用 .NET – サポートされている API</span><span class="sxs-lookup"><span data-stu-id="b326f-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="b326f-115">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="b326f-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
