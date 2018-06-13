---
title: スレッドの使用とスレッド処理
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725a47cae6e3e91cf9e7385427bceece81f3c918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584181"
---
# <a name="using-threads-and-threading"></a>スレッドの使用とスレッド処理
このセクションのトピックでは、マネージ スレッドの作成と管理、マネージ スレッドにデータを渡して結果を戻す方法、およびスレッドを破棄して <xref:System.Threading.ThreadAbortException> を処理する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [スレッドを作成し、開始時にデータを渡す](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 データを新しいスレッドに渡す方法とデータを戻す方法など、マネージ スレッドの作成について説明します。  
  
 [スレッドの一時中断と再開](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 マネージ スレッドの一時中断と再開の影響について説明します。  
  
 [スレッドの破棄](../../../docs/standard/threading/destroying-threads.md)  
 マネージ スレッドの破棄の影響と、<xref:System.Threading.ThreadAbortException> の処理方法について説明します。  
  
 [スレッドのスケジューリング](../../../docs/standard/threading/scheduling-threads.md)  
 スレッドの優先順位とスレッドのスケジューリングへの影響について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Thread> クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。  
  
 <xref:System.Threading.ThreadStart>  
 パラメーターなしのスレッド プロシージャを表す <xref:System.Threading.ThreadStart> デリゲートに関するリファレンス ドキュメントを提供します。  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 厳密な型指定はありませんが、スレッド プロシージャにデータを渡す簡単な方法を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [スレッドおよびスレッド処理](../../../docs/standard/threading/threads-and-threading.md)  
 マネージ スレッドの概要を提供します。
