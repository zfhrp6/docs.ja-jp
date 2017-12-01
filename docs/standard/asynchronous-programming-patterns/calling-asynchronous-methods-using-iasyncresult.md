---
title: "IAsyncResult を使用した非同期メソッドの呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81c05aeae00e79f614ef1514e54765b21e7e2dde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>IAsyncResult を使用した非同期メソッドの呼び出し
.NET Framework およびサード パーティ製のクラス ライブラリ内の型は、アプリケーションをアプリケーションのメイン スレッド以外のスレッドで非同期操作を実行中に実行を継続できるようにするメソッドを提供できます。 次のセクションでは、記述しを使用して非同期メソッドを呼び出すことができます、さまざまな方法を示すコード例を提供、<xref:System.IAsyncResult>デザイン パターンです。  
  
-   [非同期操作を終了してアプリケーションの実行をブロックして](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)です。  
  
-   [AsyncWaitHandle の使用、アプリケーションの実行をブロックして](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)です。  
  
-   [非同期操作のステータスのポーリング](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)です。  
  
-   [AsyncCallback デリゲートを使用して、非同期操作を終了する](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)です。  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
