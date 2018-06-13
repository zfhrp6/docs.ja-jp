---
title: クライアント側プロバイダー アセンブリの登録
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 166a2aa72fb718ee38fb6ef964179a6cd112deb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400706"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="29d9f-102">クライアント側プロバイダー アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="29d9f-102">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
>  <span data-ttu-id="29d9f-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="29d9f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="29d9f-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29d9f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="29d9f-105">このトピックでは、クライアント側 UI オートメーション プロバイダーを格納する DLL を登録する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="29d9f-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29d9f-106">例</span><span class="sxs-lookup"><span data-stu-id="29d9f-106">Example</span></span>  
 <span data-ttu-id="29d9f-107">次の例では、コンソール ウィンドウのプロバイダーを格納するアセンブリを登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29d9f-107">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="29d9f-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="29d9f-108">See Also</span></span>  
 [<span data-ttu-id="29d9f-109">クライアント側 UI オートメーション プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="29d9f-109">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
