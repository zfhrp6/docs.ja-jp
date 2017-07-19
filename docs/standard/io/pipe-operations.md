---
title: ".NET Framework でのパイプ操作 | Microsoft Docs"
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
  - "パイプ [.NET Framework]"
  - "パイプ操作 [.NET Framework]"
  - "プロセス間通信 [.NET Framework]、パイプ"
  - "I/O [.NET Framework]、パイプ"
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# .NET Framework でのパイプ操作
パイプは、プロセス間通信を行うための手段を提供します。  次の 2 種類のパイプがあります。  
  
-   匿名パイプ  
  
     匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。  匿名パイプは、名前付きパイプと比較してオーバーヘッドは小さくなりますが、提供するサービスも限定されます。  匿名パイプは一方向であり、ネットワーク経由では使用できません。  1 つのサーバー インスタンスのみをサポートします。  匿名パイプは、スレッド間または親子のプロセス間での通信に有用です。親子のプロセス間の通信では、子プロセスが作成されたときに、パイプ ハンドルを子プロセスに簡単に渡すことができます。  
  
     .NET Framework では、<xref:System.IO.Pipes.AnonymousPipeServerStream> と <xref:System.IO.Pipes.AnonymousPipeClientStream> クラスを使用して、匿名パイプを実装します。  
  
     「[方法: ローカルのプロセス間通信で匿名パイプを使用する](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)」を参照してください。  
  
-   名前付きパイプ  
  
     名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。  名前付きパイプでは、一方向または双方向のパイプを使用できます。  メッセージ ベースの通信をサポートし、複数のクライアントが同じパイプ名を使用してサーバーに対して同時に接続できます。  名前付きパイプは、偽装もサポートしています。偽装を使用すると、プロセス間接続において、リモート サーバー上で独自のアクセス許可を使用できます。  
  
     .NET Framework では、<xref:System.IO.Pipes.NamedPipeServerStream> と <xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用して、名前付きパイプを実装します。  
  
     「[方法: ネットワークのプロセス間通信で名前付きパイプを使用する](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)」を参照してください。  
  
## 参照  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)   
 [方法: ローカルのプロセス間通信で匿名パイプを使用する](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)   
 [方法: ネットワークのプロセス間通信で名前付きパイプを使用する](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)