---
title: "Windows ランタイムへの URI の引き渡し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78ba02fa227bd5c10337da0ef8b65ceab476c1ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="6884c-102">Windows ランタイムへの URI の引き渡し</span><span class="sxs-lookup"><span data-stu-id="6884c-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="6884c-103">Windows ランタイムのメソッドは絶対 URI だけを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6884c-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="6884c-104">[!INCLUDE[wrt](../../../includes/wrt-md.md)] メソッドに相対 URI を渡すと、<xref:System.ArgumentException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6884c-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="6884c-105">理由を次に示します: を使用する場合、 [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework コードで、 [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376)クラスとして表示されます<xref:System.Uri?displayProperty=nameWithType>Intellisense にします。</span><span class="sxs-lookup"><span data-stu-id="6884c-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="6884c-106"><xref:System.Uri?displayProperty=nameWithType>クラスは、相対 Uri を使用できますが、 [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376)クラスはありません。</span><span class="sxs-lookup"><span data-stu-id="6884c-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class does not.</span></span> <span data-ttu-id="6884c-107">[!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントで公開するメソッドでも同様です。</span><span class="sxs-lookup"><span data-stu-id="6884c-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="6884c-108">URI を受け取るメソッドをコンポーネントで公開する場合、コードのシグネチャには <xref:System.Uri?displayProperty=nameWithType> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6884c-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6884c-109">ただし、コンポーネントのユーザーには、署名が含まれています[Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376)です。</span><span class="sxs-lookup"><span data-stu-id="6884c-109">However, to users of your component, the signature includes [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span></span> <span data-ttu-id="6884c-110">コンポーネントに渡す URI は、絶対 URI でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6884c-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="6884c-111">このトピックでは、絶対 URI を検出する方法と、アプリ パッケージ内のリソースを参照するときに絶対 URI を作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6884c-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="6884c-112">絶対 URI の検出と使用</span><span class="sxs-lookup"><span data-stu-id="6884c-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="6884c-113">URI を <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>に渡す前にそれが絶対 URI であることを確認するには、[!INCLUDE[wrt](../../../includes/wrt-md.md)] プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="6884c-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="6884c-114">このプロパティを使用する方が、<xref:System.ArgumentException> 例外をキャッチして処理するより効率的です。</span><span class="sxs-lookup"><span data-stu-id="6884c-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="6884c-115">アプリ パッケージのリソースに対する絶対 URI の使用</span><span class="sxs-lookup"><span data-stu-id="6884c-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="6884c-116">アプリのパッケージに含まれるリソースに対して URI を指定するには、`ms-appx` スキームまたは `ms-appx-web` スキームを使用して絶対 URI を作成します。</span><span class="sxs-lookup"><span data-stu-id="6884c-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="6884c-117">次の例は、設定する方法を示します、[ソース](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx)プロパティを[WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)コントロールと[ソース](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx)プロパティを[イメージ](http://msdn.microsoft.com/library/windows/apps/br242752.aspx)コントロールXAML およびコードの両方を使用して、ページをという名前のフォルダーに含まれているリソース。</span><span class="sxs-lookup"><span data-stu-id="6884c-117">The following example shows how to set the [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="6884c-118">これらのスキームに関する詳細については、次を参照してください。 [URI スキーム](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx)、Windows デベロッパー センターにします。</span><span class="sxs-lookup"><span data-stu-id="6884c-118">For more information about these schemes, see [URI schemes](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6884c-119">参照</span><span class="sxs-lookup"><span data-stu-id="6884c-119">See Also</span></span>  
 [<span data-ttu-id="6884c-120">Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート</span><span class="sxs-lookup"><span data-stu-id="6884c-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
