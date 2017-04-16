---
title: "How to: Prevent a Child Task from Attaching to its Parent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tasks, preventing attachments"
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# How to: Prevent a Child Task from Attaching to its Parent
このドキュメントに示します。親タスクに子タスクが接続するようにする方法を示します。  子タスクがその親に役立つ接続を書き込むサード パーティによって、タスクを使用して、コンポーネントを呼び出すとされないようにです。  たとえば、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> オブジェクトを作成するために <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> オプションを使用してサードパーティのコンポーネントはコードで長時間、または未処理の例外をスローすれば問題を引き起こす可能性があります。  
  
## 使用例  
 次の例では、子タスクがその親にアタッチされることを防ぐ効果が既定のオプションを使用して結果を比較します。  この例では、<xref:System.Threading.Tasks.Task> オブジェクトを使用して、サードパーティのライブラリに <xref:System.Threading.Tasks.Task> オブジェクトを呼び出しを作成します。  サードパーティのライブラリは <xref:System.Threading.Tasks.Task> オブジェクトを作成するために <xref:System.Threading.Tasks.TaskCreationOptions> オプションを使用します。  アプリケーションは、親タスクを作成すると、<xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> オプションを使用します。  このオプションが子タスクの <xref:System.Threading.Tasks.TaskCreationOptions> 仕様を削除するようにランタイムに指示します。  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 すべての子タスクが完了するまで親タスクが完了しないため、長期間の子タスクにより、アプリケーション全体が不完全に実行できます。  この例では、アプリケーションが親タスクを作成する既定のオプションを使用する場合に、子タスクは親タスクの完了前に終了する必要があります。  アプリケーションが <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> オプションを使用すると、子は親にアタッチされません。  したがって、アプリケーションが親タスクの完了後に、子タスクを生成する前に、追加の処理を実行します。  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`DenyChildAttach.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`DenyChildAttach.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## 信頼性の高いプログラミング  
  
## 参照  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)