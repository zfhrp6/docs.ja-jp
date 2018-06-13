---
title: BackgroundWorker コンポーネント
ms.date: 03/30/2017
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
ms.openlocfilehash: 38505876e2f944139622a0d7cf7aaab9c510ef89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525753"
---
# <a name="backgroundworker-component"></a><span data-ttu-id="11900-102">BackgroundWorker コンポーネント</span><span class="sxs-lookup"><span data-stu-id="11900-102">BackgroundWorker Component</span></span>
<span data-ttu-id="11900-103">`BackgroundWorker`コンポーネントにより、フォームまたはコントロールを非同期的に操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="11900-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11900-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="11900-104">In This Section</span></span>  
 [<span data-ttu-id="11900-105">BackgroundWorker コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="11900-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="11900-106">について説明します、`BackgroundWorker`コンポーネントで、アプリケーションのメイン UI スレッドから別のスレッドで非同期的に ("バック グラウンドで")、時間のかかる操作を実行する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="11900-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="11900-107">チュートリアル: 操作をバックグラウンドで実行する</span><span class="sxs-lookup"><span data-stu-id="11900-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="11900-108">使用する方法を示します、`BackgroundWorker`コンポーネント デザイナーで、別のスレッドで時間のかかる操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="11900-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="11900-109">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="11900-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="11900-110">使用する方法を示します、`BackgroundWorker`コンポーネントを別のスレッドで時間のかかる操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="11900-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="11900-111">チュートリアル: バックグラウンド操作を使用するフォームの実装</span><span class="sxs-lookup"><span data-stu-id="11900-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="11900-112">算術計算を非同期には、デザイナーを使用してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="11900-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="11900-113">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="11900-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="11900-114">算術計算を非同期的に実行するアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="11900-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="11900-115">方法: バックグラウンドでファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="11900-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="11900-116">使用する方法を示します、`BackgroundWorker`を別のスレッド上のファイルをダウンロードするコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="11900-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11900-117">参照</span><span class="sxs-lookup"><span data-stu-id="11900-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="11900-118">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="11900-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="11900-119">データを保持する型を記述、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント。</span><span class="sxs-lookup"><span data-stu-id="11900-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="11900-120">データを保持する型を記述、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="11900-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11900-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="11900-121">Related Sections</span></span>  
 [<span data-ttu-id="11900-122">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="11900-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="11900-123">方法の非同期パターンによって利用可能な利点を活用マルチ スレッド アプリケーションの多くのマルチ スレッド デザイン固有の複雑な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="11900-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
