---
title: "方法 : マネージ HTML DOM (Document Object Model) にアクセスする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ee8c5e0cd578a0eb821a35a27c5ff0072e5533
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="0fe1d-102">方法 : マネージ HTML DOM (Document Object Model) にアクセスする</span><span class="sxs-lookup"><span data-stu-id="0fe1d-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="0fe1d-103">マネージ HTML ドキュメント オブジェクト モデル (DOM) には、次の 2 種類のアプリケーションからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
-   <span data-ttu-id="0fe1d-104">マネージ <xref:System.Windows.Forms.WebBrowser> コントロールをホストする Windows フォーム アプリケーション (.exe)。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="0fe1d-105">この 2 つのテクノロジは相互に補完します。つまり、<xref:System.Windows.Forms.WebBrowser> コントロールはユーザーに対してページを表示し、HTML DOM はドキュメントの論理構造体を表します。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
-   <span data-ttu-id="0fe1d-106">Internet Explorer 内でホストされた Windows フォーム <xref:System.Windows.Forms.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="0fe1d-107"><xref:System.Windows.Forms.UserControl> をホストするページを表す HTML DOM にアクセスして、ドキュメントの構造体を変更したり、モーダル ダイアログ ボックスを開いたりするなど、さまざまな操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="0fe1d-108">Windows フォーム アプリケーションから DOM にアクセスするには</span><span class="sxs-lookup"><span data-stu-id="0fe1d-108">To access DOM from a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="0fe1d-109">Windows フォーム アプリケーション内で <xref:System.Windows.Forms.WebBrowser> コントロールをホストし、<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントを監視します。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="0fe1d-110">コントロールのホストとイベントの監視の詳細については、「[イベント](../../../../docs/standard/events/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-110">For details on hosting controls and monitoring for events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
2.  <span data-ttu-id="0fe1d-111"><xref:System.Windows.Forms.HtmlDocument> コントロールの <xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティにアクセスして、現在のページの <xref:System.Windows.Forms.WebBrowser> を取得します。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="0fe1d-112">Internet Explorer でホストされた UserControl から DOM にアクセスするには</span><span class="sxs-lookup"><span data-stu-id="0fe1d-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="0fe1d-113"><xref:System.Windows.Forms.UserControl> クラスのカスタム派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="0fe1d-114">詳細については、「[方法: 複合コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-114">For more information, see [How to: Author Composite Controls](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span></span>  
  
2.  <span data-ttu-id="0fe1d-115"><xref:System.Windows.Forms.UserControl> の Load イベント ハンドラー内に次のコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0fe1d-116">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="0fe1d-116">Robust Programming</span></span>  
  
1.  <span data-ttu-id="0fe1d-117"><xref:System.Windows.Forms.WebBrowser> コントロールを通じて DOM を使用するときは、必ず <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントが発生するまで待機してから <xref:System.Windows.Forms.WebBrowser.Document%2A> コントロールの <xref:System.Windows.Forms.WebBrowser> プロパティにアクセスするようにします。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="0fe1d-118"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントは、ドキュメント全体が読み込まれた後で発生します。それ以前に DOM を使用すると、アプリケーション内でランタイム例外が発生する恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0fe1d-119">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0fe1d-119">.NET Framework Security</span></span>  
  
1.  <span data-ttu-id="0fe1d-120">アプリケーションまたは <xref:System.Windows.Forms.UserControl> がマネージ HTML DOM にアクセスするには、完全信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="0fe1d-121">[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] を使用して Windows フォーラム アプリケーションを配置するときは、"アクセス許可の昇格" または "信頼されたアプリケーションの配置" を使用して完全信頼を要求できます。詳細については、「[ClickOnce アプリケーションのセキュリティ](/visualstudio/deployment/securing-clickonce-applications)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe1d-121">If you are deploying a Windows Forms application using [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe1d-122">参照</span><span class="sxs-lookup"><span data-stu-id="0fe1d-122">See Also</span></span>  
 [<span data-ttu-id="0fe1d-123">マネージ HTML DOM (Document Object Model) の使用</span><span class="sxs-lookup"><span data-stu-id="0fe1d-123">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
