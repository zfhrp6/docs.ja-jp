---
title: "方法: アプリケーション リソースを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac1fa1576e684a4b10f00310c08e4e7101a5df0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="b9353-102">方法: アプリケーション リソースを使用する</span><span class="sxs-lookup"><span data-stu-id="b9353-102">How to: Use Application Resources</span></span>
<span data-ttu-id="b9353-103">この例では、アプリケーション リソースを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9353-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9353-104">例</span><span class="sxs-lookup"><span data-stu-id="b9353-104">Example</span></span>  
 <span data-ttu-id="b9353-105">次の例は、アプリケーション定義ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9353-105">The following example shows an application definition file.</span></span> <span data-ttu-id="b9353-106">アプリケーション定義ファイルは、リソース セクションを定義します (値を<xref:System.Windows.Application.Resources%2A>プロパティ)。</span><span class="sxs-lookup"><span data-stu-id="b9353-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="b9353-107">アプリケーション レベルで定義されているリソースには、そのアプリケーションの一部であるその他すべてのページからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b9353-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="b9353-108">この例では、リソースは宣言済みのスタイルです。</span><span class="sxs-lookup"><span data-stu-id="b9353-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="b9353-109">この例は省略内で定義されているコントロールのテンプレートをコントロール テンプレートを含む完全なスタイル指定できますが、時間がかかるため、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>スタイルのプロパティ set アクセス操作子。</span><span class="sxs-lookup"><span data-stu-id="b9353-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="b9353-110">次の例は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]前の例で定義されているアプリケーション レベル リソースを参照するページ。</span><span class="sxs-lookup"><span data-stu-id="b9353-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="b9353-111">使用して、リソースが参照されている、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)要求されたリソースの一意のリソース キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9353-111">The resource is referenced by using a     [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="b9353-112">"GelButton" というキーを持つリソースが、現在のページで見つからないため、要求されているリソースのリソース ルックアップ スコープは、現在のページを越えて、定義されているアプリケーション レベルのリソースまで継続されます。</span><span class="sxs-lookup"><span data-stu-id="b9353-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="b9353-113">参照</span><span class="sxs-lookup"><span data-stu-id="b9353-113">See Also</span></span>  
 [<span data-ttu-id="b9353-114">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="b9353-114">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="b9353-115">アプリケーション管理の概要</span><span class="sxs-lookup"><span data-stu-id="b9353-115">Application Management Overview</span></span>](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [<span data-ttu-id="b9353-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="b9353-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
