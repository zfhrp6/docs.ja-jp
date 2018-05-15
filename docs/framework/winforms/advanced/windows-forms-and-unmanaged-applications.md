---
title: Windows フォームとアンマネージ アプリケーション
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: c51645fb64f512b5974000f89e8e98f884a7381d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="105a3-102">Windows フォームとアンマネージ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="105a3-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="105a3-103">Windows フォーム アプリケーションとコントロールは、いくつかの注意事項がありますが、アンマネージ アプリケーションと相互運用できます。</span><span class="sxs-lookup"><span data-stu-id="105a3-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="105a3-104">次のセクションでは、Windows フォーム アプリケーションとコントロールがサポートするシナリオと構成、および、サポートしないシナリオと構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="105a3-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="105a3-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="105a3-105">In This Section</span></span>  
 [<span data-ttu-id="105a3-106">Windows フォームおよびアンマネージ アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="105a3-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="105a3-107">アンマネージ アプリケーションで使用する Windows フォーム コントロールを実装する方法に関する一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="105a3-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="105a3-108">方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする</span><span class="sxs-lookup"><span data-stu-id="105a3-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="105a3-109"><xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して Windows フォームをアンマネージ アプリケーションで実行する方法を示すコード例を提供します。</span><span class="sxs-lookup"><span data-stu-id="105a3-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="105a3-110">方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする</span><span class="sxs-lookup"><span data-stu-id="105a3-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="105a3-111">独自のスレッドで Windows フォームを実行する方法を示すコード例を提供します。</span><span class="sxs-lookup"><span data-stu-id="105a3-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="105a3-112">「 [チュートリアル: Windows フォームを別個のスレッドに表示することによって COM 相互運用をサポートする](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="105a3-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="105a3-113">参照</span><span class="sxs-lookup"><span data-stu-id="105a3-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="105a3-114">Windows フォーム用の個別のスレッドの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="105a3-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="105a3-115">スレッドのメッセージ ループを開始します。</span><span class="sxs-lookup"><span data-stu-id="105a3-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="105a3-116">フォームにアンマネージ アプリケーションからの呼び出しをマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="105a3-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="105a3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="105a3-117">Related Sections</span></span>  
 [<span data-ttu-id="105a3-118">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="105a3-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="105a3-119">.NET Framework の型をアンマネージ アプリケーションで使用する方法に関する一般情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="105a3-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
