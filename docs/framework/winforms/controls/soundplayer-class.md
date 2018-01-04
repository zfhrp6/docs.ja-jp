---
title: "SoundPlayer クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SoundPlayer
helpviewer_keywords: sounds [Windows Forms], playing
ms.assetid: f3945af9-045c-4e2d-b251-377c37ca2d77
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5379da3361a8a4b2115f46d0d2db80a565f6bfc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="soundplayer-class"></a><span data-ttu-id="90737-102">SoundPlayer クラス</span><span class="sxs-lookup"><span data-stu-id="90737-102">SoundPlayer Class</span></span>
<span data-ttu-id="90737-103">`SoundPlayer` クラスを使用すると、アプリケーションにサウンドを簡単に組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="90737-103">The `SoundPlayer` class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="90737-104"><xref:System.Media.SystemSounds> クラスを使用して、ビープ音を含む、共通のシステム サウンドを再生することもできます。</span><span class="sxs-lookup"><span data-stu-id="90737-104">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90737-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="90737-105">In This Section</span></span>  
 [<span data-ttu-id="90737-106">SoundPlayer クラスの概要</span><span class="sxs-lookup"><span data-stu-id="90737-106">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)  
 <span data-ttu-id="90737-107">クラスの概要と、一般的に使用するプロパティ、メソッド、イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="90737-107">Introduces the class and its commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="90737-108">方法: Windows フォームからサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="90737-108">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 <span data-ttu-id="90737-109">ファイル パス、UNC パス、または HTTP パスで指定したサウンドを再生するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="90737-109">Provides code to play a sound specified via a file path, UNC path, or HTTP path.</span></span>  
  
 [<span data-ttu-id="90737-110">方法: Windows フォームからビープ音を再生する</span><span class="sxs-lookup"><span data-stu-id="90737-110">How to: Play a Beep from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 <span data-ttu-id="90737-111">コンピューターのビープ音を再生するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="90737-111">Provides code to play the computer's beep sound.</span></span>  
  
 [<span data-ttu-id="90737-112">方法: Windows フォームからリソースに埋め込まれたサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="90737-112">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form.md)  
 <span data-ttu-id="90737-113">リソースからサウンドを再生するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="90737-113">Provides code to play a sound from a resource.</span></span>  
  
 [<span data-ttu-id="90737-114">方法: Windows フォームからシステム サウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="90737-114">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 <span data-ttu-id="90737-115">いずれかのシステム サウンドを再生するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="90737-115">Provides code to play the one of the system sounds.</span></span>  
  
 [<span data-ttu-id="90737-116">方法: Windows フォーム内でサウンドを非同期的に読み込む</span><span class="sxs-lookup"><span data-stu-id="90737-116">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 <span data-ttu-id="90737-117">URL からサウンドを非同期で読み込んで再生するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="90737-117">Provides code to load a sound asynchronously from a URL and play it.</span></span>  
  
 [<span data-ttu-id="90737-118">方法: Windows フォームでサウンドの再生をループする</span><span class="sxs-lookup"><span data-stu-id="90737-118">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)  
 <span data-ttu-id="90737-119">サウンドを繰り返し再生するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="90737-119">Provides code that plays a sound repeatedly.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90737-120">参照</span><span class="sxs-lookup"><span data-stu-id="90737-120">Reference</span></span>  
 <xref:System.Media.SoundPlayer>  
 <span data-ttu-id="90737-121">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="90737-121">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90737-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="90737-122">Related Sections</span></span>  
 [<span data-ttu-id="90737-123">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="90737-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="90737-124">Windows フォームでの操作専用に設計されているコントロールについてのトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="90737-124">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="90737-125">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="90737-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="90737-126">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="90737-126">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 <span data-ttu-id="90737-127">参照してください[ハイパーリンク"http://msdn.microsoft.com/library/11bxex12(v=vs.110)"My.Computer オブジェクト](http://msdn.microsoft.com/library/11bxex12\(v=vs.110\))または[My.Computer オブジェクト](http://msdn.microsoft.com/library/11bxex12\(v=vs.120\))です。</span><span class="sxs-lookup"><span data-stu-id="90737-127">Also see [HYPERLINK "http://msdn.microsoft.com/library/11bxex12(v=vs.110)" My.Computer Object](http://msdn.microsoft.com/library/11bxex12\(v=vs.110\)) or [My.Computer Object](http://msdn.microsoft.com/library/11bxex12\(v=vs.120\)).</span></span>
