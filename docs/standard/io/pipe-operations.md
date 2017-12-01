---
title: ".NET Framework でのパイプ操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a>.NET Framework でのパイプ操作
パイプは、プロセス間通信の手段を提供します。 パイプの 2 つの種類があります。  
  
-   匿名パイプします。  
  
     匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。 匿名パイプは、名前付きパイプよりもオーバーヘッドは小さくなりますが、限られたサービスを提供します。 匿名パイプは一方向であり、ネットワーク経由で使用することはできません。 1 台のサーバー インスタンスのみをサポートします。 匿名パイプは、スレッド間または場所パイプ ハンドルで簡単に渡すことが子プロセスの作成時に、親と子のプロセス間通信に便利です。  
  
     .NET framework を使用して匿名パイプを実装する、<xref:System.IO.Pipes.AnonymousPipeServerStream>と<xref:System.IO.Pipes.AnonymousPipeClientStream>クラスです。  
  
     参照してください[する方法: 匿名パイプを使用して、ローカルのプロセス間通信に](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)です。  
  
-   名前付きパイプ。  
  
     名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。 名前付きパイプには、一方向または双方向を指定できます。 メッセージ ベースの通信をサポートし、複数のクライアントが同時に同じパイプ名を使用して、サーバー プロセスに接続できます。 名前付きパイプでは、プロセスを接続してリモート サーバーで独自のアクセス許可を使用するには、偽装もサポートします。  
  
     .NET framework を使用して名前付きパイプを実装する、<xref:System.IO.Pipes.NamedPipeServerStream>と<xref:System.IO.Pipes.NamedPipeClientStream>クラスです。  
  
     参照してください[する方法: ネットワーク プロセス間通信に名前付きパイプを使用して](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)  
 [方法: ローカルのプロセス間通信で匿名パイプを使用する](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [方法: ネットワークのプロセス間通信で名前付きパイプを使用する](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
