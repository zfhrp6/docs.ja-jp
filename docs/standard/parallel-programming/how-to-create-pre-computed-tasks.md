---
title: "方法: 事前計算済みのタスクを作成する"
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
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>方法: 事前計算済みのタスクを作成する
このドキュメントを使用する方法について説明、<xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType>キャッシュ内に保持されている非同期ダウンロード操作の結果を取得します。 <xref:System.Threading.Tasks.Task.FromResult%2A>メソッドは、完成したを返します<xref:System.Threading.Tasks.Task%601>として指定された値を保持するオブジェクト、<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティです。 このメソッドは <xref:System.Threading.Tasks.Task%601> オブジェクトの結果があらかじめ計算されている <xref:System.Threading.Tasks.Task%601> オブジェクトを返す、非同期操作を実行する場合に便利です。  
  
## <a name="example"></a>例  
 次の例は、文字列を web からダウンロードします。 定義する、`DownloadStringAsync`メソッドです。 このメソッドは、非同期的に、web から文字列をダウンロードします。 またこの例では、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>以前の操作の結果をキャッシュするオブジェクト。 入力のアドレスがこのキャッシュに保持されている場合`DownloadStringAsync`を使用して、<xref:System.Threading.Tasks.Task.FromResult%2A>を生成するメソッド、<xref:System.Threading.Tasks.Task%601>そのアドレスでコンテンツを保持するオブジェクト。 それ以外の場合、 `DownloadStringAsync` web からファイルをダウンロードし、結果をキャッシュに追加します。  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 この例では、複数の文字列を 2 回ダウンロードするために必要な時間を計算します。 結果がキャッシュに保持されているために、ダウンロード操作の 2 番目のセットは、最初のセットよりも時間を短縮する必要があります。 <xref:System.Threading.Tasks.Task.FromResult%2A>メソッドにより、`DownloadStringAsync`メソッドを作成<xref:System.Threading.Tasks.Task%601>これらを保持するオブジェクトは、結果を事前計算します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`CachedDownloads.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `CachedDownloads.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
## <a name="see-also"></a>関連項目  
 [タスク ベースの非同期プログラミング](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
