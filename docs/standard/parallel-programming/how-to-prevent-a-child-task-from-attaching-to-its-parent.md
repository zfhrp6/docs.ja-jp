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
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>方法: 子タスクがその親にアタッチしないようにする
このドキュメントでは、子タスクが親タスクにアタッチされないようにする方法を示します。 サード パーティによって書き込まれ、タスクにも使用するコンポーネントを呼び出す場合は、子タスクがその親にアタッチされないようにすると便利です。 たとえばを使用してサード パーティ コンポーネント、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>を作成するオプション、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>オブジェクトで問題が発生、コードは、実行時間の長いまたは未処理の例外がスローされます。  
  
## <a name="example"></a>例  
 次の例では、効果が親にアタッチされた子タスクを回避するという既定のオプションを使用する効果を比較します。 例は、作成、<xref:System.Threading.Tasks.Task>もを使用するサード パーティ製ライブラリを呼び出すオブジェクト、<xref:System.Threading.Tasks.Task>オブジェクト。 サード パーティ製ライブラリを使用して、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>を作成するオプション、<xref:System.Threading.Tasks.Task>オブジェクト。 アプリケーションを使用して、<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>親タスクを作成するオプションです。 このオプションを削除するようランタイムに指示、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>子タスクで指定します。  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 すべての子タスクが終了するまで、親タスクが完了していないため、実行時間の長い子タスクによって生じるパフォーマンスを発揮する全体的なアプリケーションです。 この例ではアプリケーションでは、既定のオプションを使用して、親タスクを作成するときは、子タスク、親タスクが完了する前に完了する必要があります。 アプリケーションを使用する場合、<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>オプション、子が親にアタッチされていません。 そのため、アプリケーションは、親タスクが終了して、子タスクを完了を待機する前に、追加の作業を実行できます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DenyChildAttach.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DenyChildAttach.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
## <a name="see-also"></a>関連項目  
 [タスク ベースの非同期プログラミング](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
