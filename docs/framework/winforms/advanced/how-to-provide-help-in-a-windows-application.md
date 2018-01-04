---
title: "方法 : Windows アプリケーションにヘルプを提供する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d551a9d4ba6a66a02718f9184d962539361aa6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="0dc10-102">方法 : Windows アプリケーションにヘルプを提供する</span><span class="sxs-lookup"><span data-stu-id="0dc10-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="0dc10-103">使用することができます、 <xref:System.Windows.Forms.HelpProvider> Windows フォームでの特定のコントロールにヘルプ ファイル内でヘルプ トピックをアタッチするコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="0dc10-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="0dc10-104">ヘルプ ファイルの形式には、HTML または HTMLHelp 1.x 以上を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0dc10-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0dc10-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0dc10-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0dc10-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0dc10-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0dc10-107">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dc10-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="0dc10-108">ヘルプを提供するには</span><span class="sxs-lookup"><span data-stu-id="0dc10-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="0dc10-109">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.HelpProvider>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="0dc10-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="0dc10-110">コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに配置されます。</span><span class="sxs-lookup"><span data-stu-id="0dc10-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="0dc10-111">**プロパティ**ウィンドウで、設定、 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> .chm、.col、または .htm のヘルプ ファイルへのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0dc10-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="0dc10-112">フォーム上にあるし、別のコントロールを選択して、**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0dc10-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="0dc10-113">これは、を介して渡された文字列、<xref:System.Windows.Forms.HelpProvider>コンポーネント、ヘルプ ファイルに適切なヘルプ トピックをします。</span><span class="sxs-lookup"><span data-stu-id="0dc10-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="0dc10-114">**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>プロパティの値を<xref:System.Windows.Forms.HelpNavigator>列挙します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="0dc10-115">これにより、**HelpKeyword** プロパティがヘルプ システムに渡される方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="0dc10-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="0dc10-116">設定できるオプションとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="0dc10-117">メンバー名</span><span class="sxs-lookup"><span data-stu-id="0dc10-117">Member Name</span></span>|<span data-ttu-id="0dc10-118">説明</span><span class="sxs-lookup"><span data-stu-id="0dc10-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="0dc10-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="0dc10-119">AssociateIndex</span></span>|<span data-ttu-id="0dc10-120">指定したトピックのインデックスを指定した URL で実行するように指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="0dc10-121">[検索]</span><span class="sxs-lookup"><span data-stu-id="0dc10-121">Find</span></span>|<span data-ttu-id="0dc10-122">指定した URL の検索ページを表示するように指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="0dc10-123">インデックス</span><span class="sxs-lookup"><span data-stu-id="0dc10-123">Index</span></span>|<span data-ttu-id="0dc10-124">指定した URL のインデックスを表示するように指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="0dc10-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="0dc10-125">KeywordIndex</span></span>|<span data-ttu-id="0dc10-126">検索するキーワードと、指定した URL で実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="0dc10-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="0dc10-127">TableOfContents</span></span>|<span data-ttu-id="0dc10-128">HTML 1.0 ヘルプ ファイルの目次を表示するように指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="0dc10-129">トピック</span><span class="sxs-lookup"><span data-stu-id="0dc10-129">Topic</span></span>|<span data-ttu-id="0dc10-130">指定した URL によって参照されるトピックを表示するように指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="0dc10-131">F1 キーを押して、実行時にときにコントロール — 設定したため、 **HelpKeyword**と**HelpNavigator**プロパティ — がフォーカスに関連付けられているヘルプ ファイルを開きます<xref:System.Windows.Forms.HelpProvider>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="0dc10-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="0dc10-132">現在、**HelpNamespace** プロパティは HTMLHelp 1.x、HTMLHelp 2.0、および HTML の 3 つの形式のヘルプ ファイルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0dc10-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="0dc10-133">したがって、**HelpNamespace** プロパティには http:// アドレス (Web ページなど) を設定できます。</span><span class="sxs-lookup"><span data-stu-id="0dc10-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="0dc10-134">プロパティに http:// アドレスを設定すると、既定のブラウザーが開き、**HelpKeyword** プロパティに指定した文字列をアンカーとして使用して Web ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0dc10-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="0dc10-135">アンカーは HTML ページの特定の部分にジャンプするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0dc10-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0dc10-136">クライアントから送信された情報は、アプリケーションで使用する前に必ずチェックしてください。</span><span class="sxs-lookup"><span data-stu-id="0dc10-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="0dc10-137">悪意のあるユーザーが、実行可能スクリプトや SQL ステートメントなどのコードの送信 (挿入) を試みる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0dc10-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="0dc10-138">ユーザーからの入力を表示したり、データベースに格納したり、操作したりする前に、安全でない可能性のある情報が含まれていないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0dc10-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="0dc10-139">一般的な確認方法としては、ユーザーから入力を受け取ったときに、正規表現を使用して、"SCRIPT" などのキーワードを検索します。</span><span class="sxs-lookup"><span data-stu-id="0dc10-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="0dc10-140">使用することも、 <xref:System.Windows.Forms.HelpProvider> Windows フォーム上のコントロールのヘルプ ファイルを表示するよう構成されている場合でも、ポップアップのヘルプを表示するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="0dc10-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="0dc10-141">詳細については、「[方法: ポップアップ ヘルプを表示する](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dc10-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc10-142">参照</span><span class="sxs-lookup"><span data-stu-id="0dc10-142">See Also</span></span>  
 [<span data-ttu-id="0dc10-143">方法: ポップアップ ヘルプを表示する</span><span class="sxs-lookup"><span data-stu-id="0dc10-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="0dc10-144">ツールヒントを使用したコントロールのヘルプ</span><span class="sxs-lookup"><span data-stu-id="0dc10-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="0dc10-145">Windows フォームでのヘルプの統合</span><span class="sxs-lookup"><span data-stu-id="0dc10-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="0dc10-146">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="0dc10-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
