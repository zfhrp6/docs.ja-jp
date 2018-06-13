---
title: ソケット
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b234846e63eab59602069aa72125df116e30375d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398288"
---
# <a name="sockets"></a>ソケット
<xref:System.Net.Sockets> 名前空間には、Windows ソケット インターフェイスのマネージ実装が含まれます。 <xref:System.Net> 名前空間のその他すべてのネットワーク アクセス クラスは、ソケットのこの実装の上に構築されます。  
  
 .NET Framework <xref:System.Net.Sockets.Socket> クラスは、Winsock32 API が提供するソケット サービスのマネージ コード版です。 ほとんどの場合、**Socket** クラス メソッドはネイティブ Win32 の該当メソッドにデータをマーシャリングし、必要なセキュリティ チェックがあればそれを処理します。  
  
 **Socket** クラスは、同期と非同期という 2 つの基本モードに対応しています。 同期モードの場合、ネットワーク操作 (<xref:System.Net.Sockets.Socket.Send%2A> や <xref:System.Net.Sockets.Socket.Receive%2A> など) を実行する関数の呼び出しは、操作の完了を待ってから、呼び出し元のプログラムにコントロールを返します。 非同期モードの場合、このような呼び出しはすぐに返されます。  
  
## <a name="see-also"></a>参照  
 [方法: ソケットを作成する](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)
