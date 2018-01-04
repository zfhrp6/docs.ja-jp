---
title: "Windows フォーム コントロールのマルチスレッド処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="68f9c-102">Windows フォーム コントロールのマルチスレッド処理</span><span class="sxs-lookup"><span data-stu-id="68f9c-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="68f9c-103">多くのアプリケーションで行うことができます、ユーザー インターフェイス (UI) 応答性の高い別のスレッドで時間のかかる操作を実行することによってです。</span><span class="sxs-lookup"><span data-stu-id="68f9c-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="68f9c-104">多数のツールが使用できるマルチ スレッド処理など、Windows フォーム コントロールを<xref:System.Threading>名前空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッド、および`BackgroundWorker`コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="68f9c-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68f9c-105">`BackgroundWorker`コンポーネントの置換し、する機能を追加、<xref:System.Threading>名前空間および<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッドです。 ただし、これらは保持されます両方の下位互換性と将来の使用を選択した場合。</span><span class="sxs-lookup"><span data-stu-id="68f9c-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="68f9c-106">詳細については、次を参照してください。 [BackgroundWorker コンポーネントの概要](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="68f9c-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68f9c-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="68f9c-107">In This Section</span></span>  
 [<span data-ttu-id="68f9c-108">方法: Windows フォーム コントロールのスレッド セーフな呼び出しを行う</span><span class="sxs-lookup"><span data-stu-id="68f9c-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="68f9c-109">Windows フォーム コントロールにスレッド セーフな呼び出しを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="68f9c-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="68f9c-110">方法: バックグラウンド スレッドを使用してファイルを検索する</span><span class="sxs-lookup"><span data-stu-id="68f9c-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="68f9c-111">使用する方法を示します、<xref:System.Threading>名前空間および<xref:System.Windows.Forms.Control.BeginInvoke%2A>メソッドを非同期的にファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="68f9c-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="68f9c-112">参照</span><span class="sxs-lookup"><span data-stu-id="68f9c-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="68f9c-113">非同期操作のワーカー スレッドをカプセル化するコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="68f9c-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="68f9c-114">サウンドを非同期的に読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68f9c-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="68f9c-115">イメージを非同期的に読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68f9c-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="68f9c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="68f9c-116">Related Sections</span></span>  
 [<span data-ttu-id="68f9c-117">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="68f9c-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="68f9c-118">時間のかかる操作を行う方法を示しています、<xref:System.ComponentModel.BackgroundWorker>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="68f9c-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="68f9c-119">BackgroundWorker コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="68f9c-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="68f9c-120">使用する方法について説明するトピックを提供、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの非同期操作をします。</span><span class="sxs-lookup"><span data-stu-id="68f9c-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
