---
title: "HelpProvider コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23a9db5f7c5286eaab50f2499845f7294af878ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="43bc0-102">HelpProvider コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="43bc0-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="43bc0-103">Windows フォーム[HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)に HTML ヘルプ 1.x のヘルプ ファイル (HTML Help Workshop で生成された .chm ファイル、または .htm ファイル) を Windows アプリケーションに関連付けるコンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="43bc0-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="43bc0-104">さまざまな方法でヘルプを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="43bc0-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="43bc0-105">Windows フォーム上のコントロールには、状況依存のヘルプを提供します。</span><span class="sxs-lookup"><span data-stu-id="43bc0-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="43bc0-106">特定のダイアログ ボックスまたはダイアログ ボックスの特定のコントロールでは、状況依存のヘルプを提供します。</span><span class="sxs-lookup"><span data-stu-id="43bc0-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="43bc0-107">テーブルの内容、インデックス、または検索機能のメイン ページなどの特定領域へのヘルプ ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="43bc0-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="43bc0-108">ヘルプのプロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="43bc0-108">Using the Help Provider</span></span>  
 <span data-ttu-id="43bc0-109">追加する、<xref:System.Windows.Forms.HelpProvider>コンポーネントを Windows フォームのヘルプ プロパティを公開するフォーム上の他のコントロールを使用して、<xref:System.Windows.Forms.HelpProvider>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="43bc0-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="43bc0-110">これにより、Windows フォーム上のコントロールのヘルプを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="43bc0-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="43bc0-111">ヘルプ ファイルを関連付けることができます、<xref:System.Windows.Forms.HelpProvider>コンポーネントを使用して、<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="43bc0-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="43bc0-112">呼び出しによって提供されるヘルプの種類を指定する<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>から値を指定する、<xref:System.Windows.Forms.HelpNavigator>指定したコントロールの列挙。</span><span class="sxs-lookup"><span data-stu-id="43bc0-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="43bc0-113">呼び出してヘルプのキーワードまたはトピックを提供する、<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="43bc0-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="43bc0-114">必要に応じて、特定のヘルプ文字列を別のコントロールに関連付けるを使用して、<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="43bc0-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="43bc0-115">このメソッドを使用して、コントロールに関連付ける文字列は、コントロールにフォーカスがある状態で F1 キーを押したときに、ポップアップ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="43bc0-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="43bc0-116">場合<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>設定された場合、使用する必要がありますされていません。<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>ヘルプ テキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="43bc0-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="43bc0-117">両方を設定した場合<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>ヘルプ文字列ヘルプに基づいて<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>が優先されます。</span><span class="sxs-lookup"><span data-stu-id="43bc0-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43bc0-118">相対パスを使用して問題が発生する可能性があるときにヘルプ ファイルへのパスを指定するで、<xref:System.Windows.Forms.Help.ShowHelp%2A>メソッドまたは<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>のプロパティ、<xref:System.Windows.Forms.HelpProvider>コントロール。</span><span class="sxs-lookup"><span data-stu-id="43bc0-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="43bc0-119">そのため、ヘルプ ファイルを指定するファイルの絶対パスを使用することを確認します。</span><span class="sxs-lookup"><span data-stu-id="43bc0-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43bc0-120">参照</span><span class="sxs-lookup"><span data-stu-id="43bc0-120">See Also</span></span>  
 [<span data-ttu-id="43bc0-121">Windows フォーム アプリケーションのヘルプ システム</span><span class="sxs-lookup"><span data-stu-id="43bc0-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
