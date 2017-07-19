---
title: "How to: Create Pre-Computed Tasks | Microsoft Docs"
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
  - "tasks, creating pre-computed"
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Create Pre-Computed Tasks
このドキュメントでは、キャッシュに保持されている非同期ダウンロード操作の結果を取得するために <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=fullName> のメソッドを使用する方法について説明します。  <xref:System.Threading.Tasks.Task.FromResult%2A> メソッドの戻り <xref:System.Threading.Tasks.Task%601> の終了するオブジェクトを保持する <xref:System.Threading.Tasks.Task%601.Result%2A> のプロパティとして指定した値。  このメソッドは <xref:System.Threading.Tasks.Task%601> オブジェクトの結果があらかじめ計算されている <xref:System.Threading.Tasks.Task%601> オブジェクトを返す、非同期操作を実行する場合に便利です。  
  
## 使用例  
 次の例は、Web から文字列をダウンロードします。  これは `DownloadStringAsync` のメソッドを定義します。  このメソッドは、Web から文字列を非同期にダウンロードします。  この例では、前の操作の結果をキャッシュに <xref:System.Collections.Concurrent.ConcurrentDictionary%602> オブジェクトを使用します。  入力アドレスがこのキャッシュに保持されている場合、`DownloadStringAsync` はそのアドレスで <xref:System.Threading.Tasks.Task%601> オブジェクトを保持するために <xref:System.Threading.Tasks.Task.FromResult%2A> コンテンツのメソッドを使用します。  それ以外の場合は `DownloadStringAsync` は、Web からファイルをダウンロードし、結果をキャッシュに追加します。  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 この例は、複数の文字列をダウンロードするために 2 回必要な時間を計算します。  ダウンロード操作の 2 番目のセットが結果をキャッシュに保持されるため、最初の設定よりも時間がかかります。  <xref:System.Threading.Tasks.Task.FromResult%2A> のメソッドは `DownloadStringAsync` のメソッドがこれらの事前計算結果を保持する <xref:System.Threading.Tasks.Task%601> オブジェクトを作成できるようになります。  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`CachedDownloads.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`CachedDownloads.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## 信頼性の高いプログラミング  
  
## 参照  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)