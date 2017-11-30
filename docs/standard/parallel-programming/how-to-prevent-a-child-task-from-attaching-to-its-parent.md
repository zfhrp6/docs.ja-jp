---
title: "方法: 子タスクがその親にアタッチしないようにする"
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
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="fc20a-102">方法: 子タスクがその親にアタッチしないようにする</span><span class="sxs-lookup"><span data-stu-id="fc20a-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="fc20a-103">このドキュメントでは、子タスクが親タスクにアタッチされないようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fc20a-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="fc20a-104">サード パーティによって書き込まれ、タスクにも使用するコンポーネントを呼び出す場合は、子タスクがその親にアタッチされないようにすると便利です。</span><span class="sxs-lookup"><span data-stu-id="fc20a-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="fc20a-105">たとえばを使用してサード パーティ コンポーネント、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>を作成するオプション、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>オブジェクトで問題が発生、コードは、実行時間の長いまたは未処理の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fc20a-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc20a-106">例</span><span class="sxs-lookup"><span data-stu-id="fc20a-106">Example</span></span>  
 <span data-ttu-id="fc20a-107">次の例では、効果が親にアタッチされた子タスクを回避するという既定のオプションを使用する効果を比較します。</span><span class="sxs-lookup"><span data-stu-id="fc20a-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="fc20a-108">例は、作成、<xref:System.Threading.Tasks.Task>もを使用するサード パーティ製ライブラリを呼び出すオブジェクト、<xref:System.Threading.Tasks.Task>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fc20a-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="fc20a-109">サード パーティ製ライブラリを使用して、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>を作成するオプション、<xref:System.Threading.Tasks.Task>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fc20a-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="fc20a-110">アプリケーションを使用して、<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>親タスクを作成するオプションです。</span><span class="sxs-lookup"><span data-stu-id="fc20a-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="fc20a-111">このオプションを削除するようランタイムに指示、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>子タスクで指定します。</span><span class="sxs-lookup"><span data-stu-id="fc20a-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="fc20a-112">すべての子タスクが終了するまで、親タスクが完了していないため、実行時間の長い子タスクによって生じるパフォーマンスを発揮する全体的なアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="fc20a-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="fc20a-113">この例ではアプリケーションでは、既定のオプションを使用して、親タスクを作成するときは、子タスク、親タスクが完了する前に完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc20a-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="fc20a-114">アプリケーションを使用する場合、<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>オプション、子が親にアタッチされていません。</span><span class="sxs-lookup"><span data-stu-id="fc20a-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="fc20a-115">そのため、アプリケーションは、親タスクが終了して、子タスクを完了を待機する前に、追加の作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc20a-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc20a-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fc20a-116">Compiling the Code</span></span>  
 <span data-ttu-id="fc20a-117">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DenyChildAttach.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DenyChildAttach.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fc20a-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="fc20a-118">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="fc20a-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="fc20a-119">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="fc20a-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fc20a-120">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="fc20a-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc20a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc20a-121">See Also</span></span>  
 [<span data-ttu-id="fc20a-122">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="fc20a-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
