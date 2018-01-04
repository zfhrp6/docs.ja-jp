---
title: "BackgroundWorker コンポーネント"
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
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d83ff69053a71626d0bf9a844d9e94235080d78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="backgroundworker-component"></a><span data-ttu-id="b9fa8-102">BackgroundWorker コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b9fa8-102">BackgroundWorker Component</span></span>
<span data-ttu-id="b9fa8-103">`BackgroundWorker`コンポーネントにより、フォームまたはコントロールを非同期的に操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9fa8-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b9fa8-104">In This Section</span></span>  
 [<span data-ttu-id="b9fa8-105">BackgroundWorker コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="b9fa8-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="b9fa8-106">について説明します、`BackgroundWorker`コンポーネントで、アプリケーションのメイン UI スレッドから別のスレッドで非同期的に ("バック グラウンドで")、時間のかかる操作を実行する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="b9fa8-107">チュートリアル: 操作をバックグラウンドで実行する</span><span class="sxs-lookup"><span data-stu-id="b9fa8-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="b9fa8-108">使用する方法を示します、`BackgroundWorker`コンポーネント デザイナーで、別のスレッドで時間のかかる操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="b9fa8-109">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="b9fa8-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="b9fa8-110">使用する方法を示します、`BackgroundWorker`コンポーネントを別のスレッドで時間のかかる操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="b9fa8-111">チュートリアル: バックグラウンド操作を使用するフォームの実装</span><span class="sxs-lookup"><span data-stu-id="b9fa8-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="b9fa8-112">算術計算を非同期には、デザイナーを使用してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="b9fa8-113">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="b9fa8-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="b9fa8-114">算術計算を非同期的に実行するアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="b9fa8-115">方法: バックグラウンドでファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="b9fa8-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="b9fa8-116">使用する方法を示します、`BackgroundWorker`を別のスレッド上のファイルをダウンロードするコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b9fa8-117">参照</span><span class="sxs-lookup"><span data-stu-id="b9fa8-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="b9fa8-118">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="b9fa8-119">データを保持する型を記述、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="b9fa8-120">データを保持する型を記述、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9fa8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9fa8-121">Related Sections</span></span>  
 [<span data-ttu-id="b9fa8-122">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="b9fa8-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="b9fa8-123">方法の非同期パターンによって利用可能な利点を活用マルチ スレッド アプリケーションの多くのマルチ スレッド デザイン固有の複雑な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9fa8-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
